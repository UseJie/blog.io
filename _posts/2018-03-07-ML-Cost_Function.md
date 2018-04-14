---
layout: post
title: Linear regression with one variable - Cost Function
date: 2018-03-07
categories: blog
tages: [ML]
description: 
---

# Cost Function(代价函数)

# Cost function intuition  I

# Cost function intuition II

## 轮廓图(contour plot 或 contour figure)

Hypothesis:

<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>J</mi>
  <mo stretchy="false">(</mo>
  <msub>
    <mi>&#x03B8;<!-- θ --></mi>
    <mn>0</mn>
  </msub>
  <mo>,</mo>
  <msub>
    <mi>&#x03B8;<!-- θ --></mi>
    <mn>1</mn>
  </msub>
  <mo stretchy="false">)</mo>
  <mo>=</mo>
  <mstyle displaystyle="true">
    <mfrac>
      <mn>1</mn>
      <mrow>
        <mn>2</mn>
        <mi>m</mi>
      </mrow>
    </mfrac>
  </mstyle>
  <mstyle displaystyle="true">
    <munderover>
      <mo>&#x2211;<!-- ∑ --></mo>
      <mrow class="MJX-TeXAtom-ORD">
        <mi>i</mi>
        <mo>=</mo>
        <mn>1</mn>
      </mrow>
      <mi>m</mi>
    </munderover>
    <msup>
      <mfenced open="(" close=")">
        <mrow>
          <msub>
            <mrow class="MJX-TeXAtom-ORD">
              <mover>
                <mi>y</mi>
                <mo stretchy="false">&#x005E;<!-- ^ --></mo>
              </mover>
            </mrow>
            <mrow class="MJX-TeXAtom-ORD">
              <mi>i</mi>
            </mrow>
          </msub>
          <mo>&#x2212;<!-- − --></mo>
          <msub>
            <mi>y</mi>
            <mrow class="MJX-TeXAtom-ORD">
              <mi>i</mi>
            </mrow>
          </msub>
        </mrow>
      </mfenced>
      <mn>2</mn>
    </msup>
    <mo>=</mo>
    <mstyle>
      <mfrac>
        <mn>1</mn>
        <mrow>
          <mn>2</mn>
          <mi>m</mi>
        </mrow>
      </mfrac>
    </mstyle>
    <mstyle>
      <munderover>
        <mo>&#x2211;<!-- ∑ --></mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mi>i</mi>
          <mo>=</mo>
          <mn>1</mn>
        </mrow>
        <mi>m</mi>
      </munderover>
      <msup>
        <mfenced open="(" close=")">
          <mrow>
            <msub>
              <mi>h</mi>
              <mi>&#x03B8;<!-- θ --></mi>
            </msub>
            <mo stretchy="false">(</mo>
            <msub>
              <mi>x</mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mi>i</mi>
              </mrow>
            </msub>
            <mo stretchy="false">)</mo>
            <mo>&#x2212;<!-- − --></mo>
            <msub>
              <mi>y</mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mi>i</mi>
              </mrow>
            </msub>
          </mrow>
        </mfenced>
        <mn>2</mn>
      </msup>
    </mstyle>
  </mstyle>
</math>

Parameters:

Cost Founction:

Goal:


### 