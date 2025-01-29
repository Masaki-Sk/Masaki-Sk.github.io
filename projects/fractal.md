---
layout: project
type: project
image: img/fractal_logo.png
title: "Fractal"
date: 2023
published: true
labels:
  - Java
  - GitHub
summary: "An animation of fractal iteraton that I developed for programmig."
---

This is a fractal animation I wrote for the Programming A class, Waseda University. It's not particularly interesting, but it utilizes a painter for drawing, recursion for fractal generation, and a thread to update the drawing.

To give you a flavor of the code, here is an excerpt from one run:

<hr>

<pre>
import java.awt.*;
import javax.swing.*;

abstract class FractalLines {
    double x, y;
    int number_times;
    Graphics graphics;
    Color color;
    int order;

    FractalLines(Graphics g, int od, int nt, Color c) {
        graphics = g;
        order = od;
        number_times = nt;
        color = c;
    }

    void startFrom(double xx, double yy) {
        x = xx;
        y = yy;
    }

    int times (double a) {
        return (int)(a * number_times);
    }

    void draw() {
        graphics.setColor(color);
        run();
    }

    abstract void run();

    void lineTo(double dx, double dy) {
        graphics.drawLine(times(x), times(y), times(x + dx), times(y + dy));
        x += dx;
        y += dy;
    }
}

abstract class Triangle extends FractalLines {
    Triangle(Graphics g, int od, int number_times, Color c) {
        super(g, od, number_times, c);
    }

    void drawTriangle(double l) {
        lineTo(-l * 0.5, -l * Math.sqrt(3) / 2);
        lineTo(l, 0);
        lineTo(-l * 0.5, l * Math.sqrt(3) / 2);
    }
}

class Sierpiński extends Triangle {
    double initX, initY;
    double len;

    Sierpiński(Graphics g, int od, int number_times, Color c, double len, double x, double y) {
        super(g, od, number_times, c);
        initX = x;
        initY = y;
        this.len = len;
    }

    void start() {
        lineTo(-len, 0);
        lineTo(len, -len * Math.sqrt(3));
        lineTo(len, len * Math.sqrt(3));
        lineTo(-len, 0);

        fractal(order);
    }

    void fractal(int od) {
        double l = len / Math.pow(2, order - od);

        if(od == 0) {
            drawTriangle(l);
            return;
        }

        x += l / 2;
        fractal(od-1);

        x -= l;
        fractal(od-1);

        x += l / 2; y -= l * Math.sqrt(3) / 2;
        fractal(od-1);

        y += l * Math.sqrt(3) / 2;

        drawTriangle(l);
    }

    void run() {
        startFrom(initX, initY);
        start();
    }
}

class FractalPainter extends JPanel implements Runnable {
    private FractalLines ln;
    private int order = 0;
    private int maxDepth = 10;

    public FractalPainter() {
        setBackground(Color.WHITE);
    }

    public void run() {

        while (order < maxDepth) {
            try {
                Thread.sleep(1000); // 1秒ごとに再描画
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            repaint();
            order++;
        }
    }

    protected void paintComponent(Graphics g) {
        super.paintComponent(g);

        double len = 300;
        int times = 1;

        ln = new Sierpiński(g, order, times, Color.red, len, 400, 530);

        ln.draw();
    }
}

public class Fractals {
    public static void main(String[] args) {
        JFrame frame = new JFrame("drawing");
        frame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        frame.setSize(800, 600);

        FractalPainter painter = new FractalPainter();
        frame.add(painter);
        frame.setVisible(true);

        Thread thread = new Thread(painter);
        thread.start();

        try{
            thread.join();
        }catch(InterruptedException e){
            e.printStackTrace();
        }
        System.exit(0);
    }
}

</pre>

<hr>

Source: <a href="https://github.com/jogarces/ics-313-text-game"><i class="large github icon "></i>jogarces/ics-313-text-game</a>
