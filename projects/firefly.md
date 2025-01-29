---
layout: project
type: project
image: img/firefly_logo.png
title: "Firefly"
date: 2023
published: true
labels:
  - Java
  - GitHub
summary: "A firefly syncronization I wrote for programming A class"
---

This is something I wrote for the Programming A class at Waseda University. I created an animation that represents the phenomenon of fireflies' flashing gradually synchronizing.

To give you a flavor of the code, here is an excerpt from one run:

<hr>

<pre>
// Source code is decompiled from a .class file using FernFlower decompiler.
import java.awt.Color;
import java.awt.Graphics;

class FireFly {
   private int x;
   private int y;
   private double theta;
   private double omega;
   private static final int SIZE = 8;
   private static final double RATIO = 0.1;
   private static final double THRESHOLD = 10000.0;
   private static double dt = 0.5;

   FireFly(int var1, int var2) {
      this.x = var1;
      this.y = var2;
      this.theta = Math.random() * 2.0 * Math.PI;
      this.omega = Math.random() / 4.0 + 1.0;
   }

   static void setDt(double var0) {
      dt = var0;
   }

   private Color currentColor() {
      float var1 = (float)((Math.sin(this.theta) + 1.0) / 2.0);
      float var2 = (float)((Math.cos(this.theta) + 1.0) / 2.0);
      float var3 = 0.0F;
      return new Color(var1, var2, var3);
   }

   private static double mod2pi(double var0) {
      return Math.IEEEremainder(var0, 6.283185307179586);
   }

   void increment(FireFly[] var1) {
      double var2 = 0.0;
      int var4 = 0;

      for(int var5 = 0; var5 < var1.length; ++var5) {
         if (this.squareDistanceTo(var1[var5]) < 10000.0) {
            var2 += mod2pi(var1[var5].theta - this.theta);
            ++var4;
         }
      }

      double var7 = var2 / (double)var4;
      this.theta += (this.omega + 0.1 * var7) * dt;
      this.theta = mod2pi(this.theta);
   }

   private double squareDistanceTo(FireFly var1) {
      return (double)((var1.x - this.x) * (var1.x - this.x) + (var1.y - this.y) * (var1.y - this.y));
   }

   void fly() {
      switch ((int)(Math.random() * 4.0)) {
         case 0:
            ++this.x;
            break;
         case 1:
            --this.x;
            break;
         case 2:
            ++this.y;
            break;
         default:
            --this.y;
      }

   }

   void draw(Graphics var1) {
      var1.setColor(this.currentColor());
      var1.fillOval(this.x, this.y, 8, 8);
   }
}

</pre>

<hr>

Source: <a href="https://github.com/jogarces/ics-313-text-game"><i class="large github icon "></i>jogarces/ics-313-text-game</a>

