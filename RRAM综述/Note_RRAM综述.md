# Resistive Memory-Based Analog Synapses

><font face="Times New Roman" >Woo J, Yu S. Resistive memory-based analog synapse: The pursuit for linear and symmetric weight update[J]. IEEE Nanotechnology magazine, 2018, 12(3): 36-44.</font>
***
- **写作目的：**
  本文简介RRAM在模拟突触，实现神经形态运算方面的应用。重点讨论如何优化RRAM在模拟突触时的对称性与线性。

- **内容记录：**
    - RRAM实现模拟突触的理想特性：**线性**与**对称性**：
    
      <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig1.png" alt="fig1" style="zoom: 50%;" />
    
    - **Interface-RRAM**实现模拟突触的特性（不具有良好的对称性与线性）：
    
      <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig2.png" alt="蜂蜜浏览器_fig2" style="zoom: 67%;" />
    
    - CF-RRAM对连续脉冲的响应（仅响应第一个Set脉冲，持续响应Reset脉冲）：
    
      <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig3.png" alt="fig3" style="zoom: 67%;" />
    
    - 通过调制脉冲改变CF-RRAM对连续Set脉冲的响应：
    
      1. 使用Set+Reset脉冲实现电导的线性变化。
    
      2. 在Set过程中附加heating pulse增大电导变化范围。
    
         <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig4.png" alt="fig4" style="zoom:67%;" />
    
    - 2类CF实现的模拟突触特性（多条弱导电纤维更优）：
    
      ![fig5](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig5.png)

- **批注：**
  - 模拟突触（Analog Synapses）本质上利用的是RRAM的MLC（但也不完全相同）。
  - 线性与对称性的本质含义是希望在Set与Reset过程中，每一脉冲引起的电导变化是相同的。
  - CF-RRAM对连续脉冲的响应表明可以直接通过连续的Reset脉冲实现RRAM在Reset过程中的线性。

***

# Analog-Type Resistive Switching Devices for Neuromorphic Computing  

><font face="Times New Roman">Zhang W, Gao B, Tang J, et al. Analog‐type resistive switching devices for neuromorphic computing[J]. physica status solidi (RRL)–Rapid Research Letters, 2019, 13(10): 1900204.</font>
---
- **写作目的：**

  本文主要介绍模拟型RRAM的若干种模拟开关机制，并针对模拟型RRAM在神经形态计算方面的应用提出优化建议。

- **内容记录：**

  - 4种类型的RRAM（按**SR特性**分类）：二进制开关RRAM（用于数据存储）、多位开关RRAM（用于数据存储）、单向模拟开关RRAM、双向模拟开关RRAM：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig6.png" alt="fig6" style="zoom:80%;" />

  - 2类用于实现神经形态计算的神经网络：DNN、SNN：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig7.png" alt="fig7" style="zoom:67%;" />

  - 改进模拟型RRAM开关特性的4种方法（改进其**对称性**与**线性**）：

    1. 多条弱导电纤维（$\text{HfO}_\text{x}$）

    2. 调制导电纤维的横向延伸（$\text{HfO}_2$）
  
    3. 双原子通道（$\text{TaO}_\text{x}$）
  
    4. Interface-RRAM（$\text{Al/PCMO+N-rich TiN}$）
  
       ![fig8](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig8.png)
  
    - 使用电流脉冲及可变的栅极电压实现DNN中对应突触权重的线性与对称性：
  
      <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig9.png" alt="fig9" style="zoom:80%;" />
  
- **批注：**

  - **突触可塑性**（synaptic plasticity）：指神经细胞间的连接，即突触，其连接强度可调节的特性，可用模拟型RRAM电导可调节的特性进行模拟。
  - CF-RRAM的Set是一个正反馈过程，CF的形成使温度与局部电场增加，进而促进氧空位的增加与CF的形成，这也是导致CF-RRAM模拟开关特性具有非线性的一个主要原因。
  - 有关电流脉冲：电流脉冲的大小由外加的MOSFET调制，以Set过程为例，由于$P=I^2/G$，Set过程中电导$G$逐渐变大，因此需要调制使$I$也逐渐变大，以使$P$实现线性变化。因此需要在MOSFET栅极施加逐渐变大的栅极电压。


---

#Synaptic electronics: materials, devices and applications  
><font face="Times New Roman">Kuzum D, Yu S, Wong H S P. Synaptic electronics: materials, devices and applications[J]. Nanotechnology, 2013, 24(38): 382001.</font>
---
- **写作目的：**

  介绍**突触电子学**（Synaptic electronics）的相关内容，主要包括：可用于模拟突触的相关器件、突触器件的性能指标、包含突触器件的相关计算应用。

- **内容记录：**

  - **STDP**（spike-timing-dependent plasticity）：突触权重受前后神经元尖峰脉冲的时间差的调制：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig10.png" alt="fig10" style="zoom:80%;" />

  - 几种用于模拟STDP的器件：PCM、RRAM、CBRAM、FeRAM、FET。

    1. **PCM**：温度调制，具有较高的可扩展性、可靠性、耐久性、良好的MLC性能及器件间的均匀性：

       <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig11.png" alt="fig11" style="zoom:50%;" />

       PCM实现STDP的几种途径：多脉冲、单脉冲（通过前置的通信信号）、双PCM：

       ![蜂蜜浏览器_fig12](https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig12.png)

    2. **RRAM**：电压/电流调制，具有出色的可扩展性、较高的开关速度、良好的耐久性与**较低的能耗**。下图是几种不同氧化层材料的RRAM实现STDP的方案：

       ![蜂蜜浏览器_fig13](https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig13.png)

    3. **CBRAM**：电压调制，相当于阳离子驱动的RRAM。

    4. **FET**：

       ![fig14](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig14.png)

  - 用于实现STDP的器件的性能指标：(1)**尺寸**(2)**能耗**（最具挑战性，一般通过最小化编程时间来降低）(3)**运行速度/编程时间**（与能耗权衡）(4)**多级状态**（至少100级）(5)**动态范围**（HRS/LRS）(6)**耐久性**(7)**均匀性**。
  - 用于实现STDP的器件的理想性能指标：

  ![fig15](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig15.png)

- **批注：**

  - 突触通过调整其连接强度来调制其在计算中的权重（突触可塑性）。
  - STDP因其简单性、生物学合理性以及良好的运算性能受到广泛的关注。
  - 需要注意的一点：用于模拟突触的器件单元通常为**二端器件**（记二端为A,B端）则在A端施加正/负脉冲与在B段施加负/正脉冲是等效的（当然，这基于器件的对称性）。
  - PCM实现STDP的单脉冲方案：本质上将STDP中的**时间差**转化为了**脉冲幅度差**，给出一系列幅度的连续脉冲（包含Set与Reset），使前后脉冲在不同时间差下对应叠加的脉冲幅度不同。缺点是会有很多额外的无效脉冲，会增加能耗与干扰：

  ![fig16](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig16.jpg)

---

