#Design-Technology Co-Optimizations (DTCO) for General-Purpose Computing In-Memory Based on 55nm NOR Flash Technology  
><font face="Times New Roman" >Feng Y, Chen B, Liu J, et al. Design-Technology Co-Optimizations (DTCO) for General-Purpose Computing In-Memory Based on 55nm NOR Flash Technology[C]//2021 IEEE International Electron Devices Meeting (IEDM). IEEE, 2021: 12.1. 1-12.1. 4.</font>

***

- **写作目的：**

  本文主要讨论基于55nm的 NOR flash（一种通用的CIM架构）的内存计算，并基于DTCO提出改善NOR flash性能的一些方法并予以实验验证。

- **内容记录：**

  - 55nm NOR flash的架构设计（1个存储单元表示4位数据（16个状态，QLC））：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164234324.png" style="zoom:150%;" />

  - 使用**热空穴注入（HHI）**实现对单个存储单元的擦除操作（因为HHI是对栅极与漏极施加偏压，这两者分别与字线与位线相连，1条字线与1条位线恰好对应一个存储单元）：

  ![image-20220821164513760](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164513760.png)

  - 对55nm NOR flash全面的可靠性表征，包括：保留特性，读取干扰（read disturbs, RD），随机信号噪声，耐久性。
  - 将读写操作的工作区域由亚饱和区转至亚阈区后，存储器对应性能的比较（亚阈区工作功耗更低，但相对应的精确性降低，干扰增加）：

  ![image-20220821164553614](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164553614.png)

- **批注：**

  - **DTCO（设计工艺协同优化）**：指在选择设计方案与工艺方案时，工艺和设计相互协同，彼此协作满足新节点器件的要求。
  - flash存储单元的几种数据存储密度：

  ![image-20220821164659896](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164659896.png)

  - 一般的NOR flash使用**热电子注入（CHEI）**实现对单个存储单元的写入操作，使用量子隧穿实现对**同一字线上所有存储单元的擦除操作**；一般的NAND flash的写入原理与NOR flash相同，而擦除是基于CHEI实现的。
  - 似乎本文对DTCO仅仅是提及，并没有结合工作进行详细的说明。

---

#Implementation of Discrete Fourier Transform using RRAM Arrays with Quasi-Analog Mapping for HighFidelity Medical Image Reconstruction  

><font face="Times New Roman" >Zhao H, Liu Z, Tang J, et al. Implementation of Discrete Fourier Transform using RRAM Arrays with Quasi-Analog Mapping for High-Fidelity Medical Image Reconstruction[C]//2021 IEEE International Electron Devices Meeting (IEDM). IEEE, 2021: 12.4. 1-12.4. 4.</font>

---

- **写作目的：**

  本文主要讨论利用RRAM阵列实现**离散Fourier变换（DFT）**，提出了一种新型的电导映射方法——**准模拟映射（quasi-analog mapping, QAM）**并将其性能与常用的**量化映射（quantized mapping, QM）**进行对比。

- **内容记录：**

  - 使用RRAM阵列实现DFT的原理，每个存储单元需要的电导状态数会随DFT数据点的增加而迅速增加：

  ![image-20220821165036246](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165036246.png)

  - **QAM**与**QM**的对比：QAM（准模拟映射）其实就是以实际需要的电导值作为电导状态，并以之为中心设定写入裕度，QM（量化映射）则是预先设定好电导状态与写入裕度，而将需要的电导值量化至预先设定的电导状态，从电导状态的精确度来看，QAM会优于QM。

  ![image-20220821165117432](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165117432.png)

  - 用于实现DFT的1T1R RRAM阵列及其TEM图像：

  ![image-20220821165138060](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165138060.png)

  - 2D-DFT的具体实现原理：

  ![image-20220821165159408](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165159408.png)

- **批注：**

  - QM一般用于实现DNN，因为DNN只对最终的分类精度有要求，而对矩阵的精度没有过于严格的要求，因此可以对矩阵元素的权重进行合理的量化，而对DFT，其变换矩阵的精度很大程度上影响了变换结果的精度，因此需要使用QAM提升矩阵元素权重的精度。
  - 采用QAM进行映射消耗的能量一般高于QM，但由于在DFT算法中，对变换矩阵的映射是一次性的，因此这种能量消耗的增加相比对应性能的提高，一般是可接受的。
  - INTRODUCTION Para2 Line10中的Fig. 4可能有误，应为Fig. 3。

---

#An 8-Mb DC-Current-Free Binary-to-8b Precision ReRAM Nonvolatile Computing-in-Memory Macro using Time-SpaceReadout with 1286.4 - 21.6TOPS/W for Edge-AI Devices  
> <font face="Times New Roman" >Hung J M, Huang Y H, Huang S P, et al. An 8-Mb DC-Current-Free Binary-to-8b Precision ReRAM Nonvolatile Computing-in-Memory Macro using Time-Space-Readout with 1286.4-21.6 TOPS/W for Edge-AI Devices[C]//2022 IEEE International Solid-State Circuits Conference (ISSCC). IEEE, 2022, 65: 1-3.</font>

---

- **写作目的：**

  本文主要对提升nvCIM性能的3个方案进行了介绍，分别为DCFTS-IMC、IVTC与HLTMC。

- **内容记录：**

  - current mode nvCIM面对的挑战：因直流导致的高计算与读取能耗；输出精度；单位计算周期内较长的计算延迟：

  ![image-20220821165949703](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165949703.png)

  - 使用DCFTS-IMC方案避免使用直流电流，降低能耗：

  ![image-20220821170020327](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170020327.png)

  - 在DCFTS-IMC方案中：

    1个计算周期=**输入计算阶段**（BIC-P）+**移位加法阶段**（DSA-P）=**外围电路复位**（SP-0）+**位线预充电**（SP-1）+**字线输入**（SP-2）+**移位加法阶段**（DSA-P）

  - 使用IVTC方案增加信号裕度，提高输出精度：

  ![image-20220821170150080](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170150080.png)

  - 使用HLTMC方案缩短计算延迟：

  ![image-20220821170210031](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170210031.png)

- **批注：**

  - IVTC方案的本质，其实就是通过对电流积分获得累积电荷量，这通过对前文图中的电容$C_2$充电实现，并将累积电荷量线性转化为电压$U$，通过电压$U$与某一阈值对比确定pMACV的取值，而这与直接通过$DL$电压与阈值比较确定pMACV取值相比有更大裕度：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170346633.png" alt="image-20220821170346633" style="zoom:150%;" />

  - 本文的结构比较独特，整篇论文其实是对5张图的描述，而图中蕴含的信息量较大，分别从nvCIM面对的挑战，3种具体的方案设计以及测试评估进行描述。

---

#A 13.7 TFLOPS/W Floating-point DNN Processor using Heterogeneous Computing Architecture with Exponent-Computing-in-Memory  
><font face="Times New Roman" >Lee J, Kim J, Jo W, et al. A 13.7 TFLOPS/W floating-point DNN processor using heterogeneous computing architecture with exponent-computing-in-memory[C]//2021 Symposium on VLSI Circuits. IEEE, 2021: 1-2.</font>

---

- **写作目的：**

  本文主要提出了一种使用指数计算内存（CIM）和尾数处理引擎的异构 bfloat16 计算架构。能够有效降低存储芯片的能耗并提高计算效率。

- **内容记录：**

  - 浮点数（FP）进行乘累加（MAC）运算时，指数与尾数涉及的运算。可见指数仅涉及加减，而尾数由于需实现相乘，需实现移位、加、减等运算：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231032810.png" alt="image-20220823231032810" style="zoom:150%;" />

  - 传统的FP-CIM需要实现对指数与尾数的运算，因此耗费周期数较多，能耗较大，结构较为复杂。
  - 处理器的整体架构：

  ![image-20220823231130448](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231130448.png)

  1. **异构计算架构**，包括**指数内存计算**（ECIM）与**尾数处理引擎**（MPE），能够有效降低能耗。
  2. 采用**无尾数指数计算**（MFEC），能够最小化指数与尾数间的通信代价，同时降低MAC能耗。
  3. 位线电荷复用，可降低总体访问能耗。

  - MFEC的具体原理，实现指数与尾数运算的相互隔离：

  ![image-20220823231520241](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231520241.png)

  - 运算时序图，使用流水线以提高运算效率，减少运算耗费的周期数：

  ![image-20220823231542814](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231542814.png)

- **批注：**

  - **bfloat16（BF16）**：一种深度学习中常用的浮点数格式，共16位其中有1位符号位，8位指数位与7位尾数位。
  - 低能耗、高精度、高效率一般是CIM技术的3种主要的改进方向，主要可以从CIM架构设计、算法设计、运算时序设计等方向进行优化。

---

#A 1.041-Mb/mm2 27.38-TOPS/W Signed-INT8 Dynamic-LogicBased ADC-less SRAM Compute-In-Memory Macro in 28nm with Reconfigurable Bitwise Operation for AI and Embedded Applications  
><font face="Times New Roman" >Yan B, Hsu J L, Yu P C, et al. A 1.041-Mb/mm 2 27.38-TOPS/W Signed-INT8 Dynamic-Logic-Based ADC-less SRAM Compute-in-Memory Macro in 28nm with Reconfigurable Bitwise Operation for AI and Embedded Applications[C]//2022 IEEE International Solid-State Circuits Conference (ISSCC). IEEE, 2022, 65: 188-190.</font>

---

- **写作目的：**

  本文主要介绍一种基于**动态逻辑**（Dynamic Logic）的无ADC的SRAM CIM宏，并与传统设计进行了性能对比。

- **内容记录：**

  - 无ADC SRAM CIM宏的总体架构：

    **外围电路**包括：字线驱动器与CIM输入控制（WLDCIC）、输入组合逻辑（ICL）、内存读写电路。

    **内部存储单元**由：6T SRAM单元+4T RPLU构成。

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig.png" alt="蜂蜜浏览器_fig" style="zoom: 50%;" />

  - 动态逻辑计算电路（DCC）与本地可重构处理单元（RPLU）的机制：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823232331678.png" alt="image-20220823232331678" style="zoom:150%;" />

  - RPLU主要的工作机制是：通过输入逻辑电路（ICL）控制RPLU内部FET的开闭，从而实现不同的位运算（AND/XOR/OR）。
  - DCC的使用取代了ADC，减少了芯片占用面积；RPLU的使用使得运算可重构。
  - Post-sum电路设计，减少内存访问，提高空间利用效率：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823232433938.png" alt="image-20220823232433938" style="zoom:150%;" />

- **批注：**

  - 一般含有ADC的CIM架构，由于ADC的加入，外部电路会占据较大的空间，解决方法主要有以下几条：

    1. 使用基于**检测放大器**的处理方案。
    
    > <font face="Times New Roman" >Yan B, Li B, Qiao X, et al. Resistive Memory‐Based In‐Memory Computing: From Device and Large‐Scale Integration System Perspectives[J]. Advanced Intelligent Systems, 2019, 1(7): 1900068.</font>
    
    2. 使用全数字CIM设计。
    3. 使用本文中提及的动态逻辑计算电路（DCC）。
    
  - **VHP**：向量Hadamard积，即向量按元素相乘，其结果仍为向量。

---

#Unassisted True Analog Neural Network Training Chip  

> <font face="Times New Roman" >Kohda Y, Li Y, Hosokawa K, et al. Unassisted true analog neural network training chip[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.2. 1-36.2. 4.</font>

---

- **写作目的：**

  本文主要介绍一种单纯借助模拟cross-point阵列实现MAC的神经网络训练芯片。

- **内容记录：**

  - 本文给出的cross-point阵列单元设计：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823233032859.png" alt="image-20220823233032859" style="zoom:150%;" />

  - 基于文献：

  > <font face="Times New Roman" >Kohda Y, Li Y, Hosokawa K, et al. Unassisted true analog neural network training chip[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.2. 1-36.2. 4.</font>

  - 给出了这一阵列单元的简化结构：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823233246676.png" alt="image-20220823233246676" style="zoom:150%;" />

  ​		

  - 删去用于给反相器供电的线路，阵列单元可进一步简化为：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823233316868.png" alt="image-20220823233316868" style="zoom:150%;" />

  - 其中由YW输入差模信号使电流源输出恒定电流给电容$C$充电，电容$C$的电荷$Q$$/$电压$V_\text{cap}$表征了该单元的权重，且权重大小与输入脉冲的总脉宽呈正比。右侧的FET用于读出，而本文给出的cross-point阵列单元的右侧较为复杂，这主要是为实现训练NN时的前向传播过程与反向传播过程，前向传播时，$Xr$为输入，$Yr$为输出，$T5$、$T6$关闭，$T7$开启；反向传播时，$Yr$为输入，$Xr$为输出，$T5$、$T7$关闭，$T6$开启。
  - 本文中所使用的N×N cross-point阵列，其实就相当于一个N输入N输出的全连接层。
  - 用于训练NN的BP算法，这基于文献：

  > <font face="Times New Roman" >Gokmen T, Vlasov Y. Acceleration of deep neural network training with resistive cross-point devices: Design considerations[J]. Frontiers in neuroscience, 2016, 10: 333.</font>

  - 每一训练周期共分为3个过程：**正向传播过程**，**反向传播过程**，**权重更新过程**，这里主要考虑权重更新过程，由于一个N$\times$N cross-point阵列仅对应神经网络中的1个2层结构，于是权重更新可表示为：

  $$
  w_{ij}\leftarrow w_{ij}+\eta x_i\delta_j
  $$

  

  - 其中η为全局学习率，**可通过调整电流源的差模输入信号或调整后方的乘数进行改变**。同时，可对该权重更新方法进行简化：

  $$
  w_{ij}\leftarrow w_{ij}\pm\Delta w_\text{min}\sum\limits_{n=1}^{BL}A_i^n\wedge B_j^n
  $$

  - 使用随机比特流进行乘法运算，这基于文献：

  > <font face="Times New Roman" >Alaghi A, Hayes J P. Survey of stochastic computing[J]. ACM Transactions on Embedded computing systems (TECS), 2013, 12(2s): 1-19.</font>

  - 该文献中提出的一种仅使用AND门实现的随机乘法器（**近似运算**），2个随机比特流中含1的概率为$p_1$与$p_2$，则在通过AND门后的比特流含1的概率为$p_1p_2$，此即实现乘法：

  ![image-20220823234402565](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823234402565.png)![image-20220823234409106](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823234409106.png)

  - 测试用的模拟ASIC设计：

  ![image-20220823234430743](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823234430743.png)

  - 读上图可知，使用3个模拟cross-point阵列，实现一个单隐层的NN，隐层包含100个神经元。最终使用标准MNIST数据集进行测试。准确率为92.7%。

- **批注：**

  - 一般用于训练NN的BP算法的实现：（这里对各变量采用神经网络中的常用记号）

    - **前向传播：**即使用一个样本对神经网络进行一次输入，计算各神经元的输出：

    $$
    \left\{\begin{matrix}
     z^{(l)}=w^{(l)}a^{(l-1)}+b\\
    a^{(l)}=\sigma(z^{(l)})
    \end{matrix}\right.
    $$

    

    - **后向传播：**计算该样本对应的输出层及隐层误差：

    $$
    \delta^{(L)}=\nabla _{a^{(L)}}C(\theta)\odot\sigma'(z^{(L)})\\
    \delta^{(l)}=((w^{(l+1)})^T\delta^{(l+1)})\odot\sigma'(z^{(l)})
    $$

    - **权重更新：**更新权重：

    $$
    \left\{\begin{matrix}
    w_{jk}^{(l)}:=w_{jk}^{(l)}-\alpha a_{k}^{(l-1)}\delta_j^{(l)}\\
    b_j^{(l)}:=b_j^{(l)}-\alpha\delta_j^{(l)}
    \end{matrix}\right.
    $$

  - 其中，前向传播与后向传播基本仅涉及VMM运算，易于使用cross-point阵列实现，而权重更新涉及到对单个阵列单元的处理，以及数乘运算。

  - **MNIST数据集**：美国国家标准与技术研究院收集整理的大型手写数字数据库，研究中常使用该数据集对NN进行训练，以NN识别手写数字的准确率作为NN性能的一个可视化指标。

- **文章创新点：**

  - 所有MAC均在模拟cross-point阵列上进行实现，无需数字系统的辅助。（但这种系统在权重更新时必须本身具有良好的对称性与线性，因此阵列单元的复杂度会上升）
  - 使用随机乘法器简化权重更新时的乘法运算。

---

# High-Density 3D Monolithically Integrated Multiple 1T1R MultiLevel-Cell for Neural Networks  

><font face="Times New Roman" >Esmanhotto E, Brunet L, Castellani N, et al. High-density 3D monolithically integrated multiple 1T1R multi-level-cell for neural networks[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.5. 1-36.5. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于1T1R单元的3D RRAM阵列，能够实现阵列的高密度。同时基于该阵列研究了MLC（多位）编程后电导弛豫现象对器件存储位数与精度的影响。

- **内容记录：**

  - 对一些用于NN的RRAM的对比：

    1. 基于文献：
    
       > <font face="Times New Roman" >Robayo D A, Sassine G, Lopez J M, et al. Reliability and Variability of 1S1R OxRAM-OTS for High Density Crossbar Integration[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 35.3. 1-35.3. 4.</font>
    
       文献中给出的1S1R1T单元，其中1S指Ovonic 阈值开关(OTS)，可以有效限制未选择单元存在的隐藏路径电流：
    
       ![image-20220824233020858](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233020858.png)
    
       OTS的几种可能物理机制基于文献：
    
       > <font face="Times New Roman" >Zhu M, Ren K, Song Z. Ovonic threshold switching selectors for three-dimensional stackable phase-change memory[J]. MRS Bulletin, 2019, 44(9): 715-720.</font>
    
       主要有**thermal runaway模型**（热力学角度）、**field-induced nucleation模型**（晶体结构角度）、**electronic模型**（载流子角度）：
    
       ![image-20220824233147483](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233147483.png)
    
    2. 基于文献：
    
       > <font face="Times New Roman" >Hsieh E R, Giordano M, Hodson B, et al. High-density multiple bits-per-cell 1T4R RRAM array with gradual SET/RESET and its effectiveness for deep learning[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 35.6. 1-35.6. 4.</font>
    
       文献给出的1T4R单元设计，增加RRAM单元密度，但同时需要重新制定编程方案，同时相邻单元间由于共用1T会有干扰：
    
       ![image-20220824233348347](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233348347.png)
    
    3. 本文中提出的1T1R单元3D RRAM架构：
    
       ![image-20220824233407022](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233407022.png)
    
       相对平面RRAM位密度增加1.5倍。
    
  - 本文给出的2种电导映射方案：
  
    ![image-20220824233436411](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233436411.png)
  
    1. 基于均值与方差的映射（**SBA**），每一电导水平由以下区间给出：
       $$
       \mu_i-\Delta\sigma_i<G<\mu_i+\Delta\sigma_i
       $$
       其中$\mu_i$为均值，$\Delta\sigma_i$为方差。
  
    2. 线性映射（LA）。
  
    在MLC编程时利用上图所示的迭代编程方案实现电导水平的调整。
  
  - 对MLC编程后电导弛豫现象的研究：
  
  ![image-20220824233950102](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233950102.png)
  
  - 对2种电导映射方案（SBA/LA）的电导弛豫现象（t=60s后）的研究，较低水平的电导会发生较大偏移，无法使用：
  
  ![image-20220824234017394](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824234017394.png)
  
  - 验证电导弛豫现象并非由于设计问题导致，验证方法是对比不同设备的电导弛豫，显示该现象从设备到设备的均匀性。
  - 分别在MNIST数据集与ECG数据集上训练全连接NN，显示电导弛豫现象对NN应用的准确性影响不大。
  
- **批注：**

  - 有关电导水平与表示位数的关系：一般RRAM单元若能够表示$N$个电导水平，则代表其能够表示的位数为$\log_2N$，比如本文中的9位电导水平，其能实现3.17位的存储。
  - RRAM存储密度的提升主要基于2个方面：其一是对硬件架构的设计，使单位空间能容纳更多存储单元，其二是对单元多位存储能力的提升，使RRAM单元能够具有尽可能多的电导水平。
  - **BER（Bit Error Rate）**：用于衡量RRAM编程的准确性，数学上等于RRAM阵列编程错误的单元数与RRAM阵列的总单元数的比值，本文中认为BER<$10^{-3}$时符合要求。
  - 为什么电导弛豫现象对NN训练的准确率影响不大？因为**NN只对最终的分类精度有要求**，而对矩阵的精度没有过于严格的要求，因此可以对矩阵元素的权重进行一定程度的容错。而既然NN训练对电导弛豫现象有弹性，那么尽可能地增加RRAM单元的电导水平数便有利于增加NN最终的分类精度。

- **文章创新点：**

  - 设计了一种新型 3D（双层）RRAM架构，将 RRAM 的位密度相对于平面 RRAM 提高 1.5 倍。
  - 将 MLC 编程与 3D RRAM 设计综合应用，进一步提升 RRAM 的存储密度。
  - 将 RRAM 应用于对电导弛豫弹性较大的 NN 训练上。

---

#Fully Integrated Spiking Neural Network with Analog Neurons and RRAM Synapses  

><font face="Times New Roman" >Valentian A, Rummens F, Vianello E, et al. Fully integrated spiking neural network with analog neurons and RRAM synapses[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 14.3. 1-14.3. 4.</font>

---

- **写作目的：**

  本文主要使用RRAM实现**脉冲神经网络（SNN）**的一次完整集成。实验实现的NN结构为感知机，并使用MNIST数据集进行训练，训练后实现了84%的分类准确率。

- **内容记录：**

  - 基于N2D2（Neural Network Design and Deployment）学习框架实现SNN：

    ![image-20220824234724627](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824234724627.png)

    首先，使用**BP算法**训练DNN，其次，将DNN中的相关变量（权重，输入，输出，阈值等）转换（等价映射）至SNN中。

  - 基于文献：

    > <font face="Times New Roman" >Pérez-Carrasco J A, Zhao B, Serrano C, et al. Mapping from frame-driven to frame-free event-driven vision systems by low-rate rate coding and coincidence processing--application to feedforward ConvNets[J]. IEEE transactions on pattern analysis and machine intelligence, 2013, 35(11): 2706-2719.</font>

    文献给出了将一般NN中的变量映射至SNN中的方法：

    ![image-20220824235040435](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824235040435.png)![image-20220824235046328](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824235046328.png)

  - SNN的突触的物理结构：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig1.png" alt="蜂蜜浏览器_fig1" style="zoom: 33%;" />

  - 本文中使用单极RRAM（SLC）单元实现突触，为实现多个权重水平，使用8个单极RRAM单元共同实现1个突触：

  ![image-20220824235321403](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824235321403.png)

- **批注：**

  - 一般NN的神经元模型被称为**帧驱动模型**（frame-driven），而SNN使用的是如下所示的**事件驱动模型**（event-driven）:

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/figx.png" alt="figx" style="zoom:50%;" />

  - 该模型主要可实现如下功能：

  ![蜂蜜浏览器_fig3](https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig3.png)

- **文章创新点：**

  - 首次在RRAM上完整集成了脉冲神经网络。降低了编程所需的功耗。
  - 使用多个单极RRAM实现MLC编程以模拟突触，增加了RRAM的单元密度。

---

# ECRAM as Scalable Synaptic Cell for High-Speed, Low-Power Neuromorphic Computing

><font face="Times New Roman" >Tang J, Bishop D, Kim S, et al. ECRAM as scalable synaptic cell for high-speed, low-power neuromorphic computing[C]//2018 IEEE International Electron Devices Meeting (IEDM). IEEE, 2018: 13.1. 1-13.1. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于$\text{Li}^+$嵌入$\text{WO}_3$的ECRAM（电化学存储器），能够实现高速、低功耗的神经形态计算。

- **内容记录：**

  - ECRAM单元的三端器件结构：

    ![image-20220825093358194](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093358194.png)

    当读取时，连接源极与漏极，读取该器件的静态电导值作为结点的权重；当编程时，连接漏极与栅极，在栅极电流输入的控制下使Li+嵌入WO3中，改变器件电导。器件的完整结构：

    ![image-20220825093507972](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093507972.png)

    同样需要外接电流源对栅极电流进行控制，电流源由FET组成。

  - 分别研究器件单元权重状态数、权重更新时的对称性、器件随机性在使用MNIST数据集训练时对分类精度的影响：

  ![image-20220825093547819](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093547819.png)![image-20220825093552208](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093552208.png)![image-20220825093558877](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093558877.png)

  - ECRAM在权重更新对称性上与其余器件的对比，可见**多端器件**的优势所在：

  ![image-20220825093623585](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093623585.png)

- **批注：**

  - 三端器件与二端器件作为RAM单元的对比：
    1. **二端器件**：常见的有RRAM、FeRAM、PCM等，二端器件的优势在于结构简单，易于集成，存储密度也相应较大。但相对应的在物理上的随机性与不均匀性也较为明显，通常需要更为复杂的算法或外部电路进行调制。（因其本身其实可以说是基于缺陷设计的器件）
    2. **三端/多端器件**：常见的是FET构成的单元，三端/多端器件的优势在于可以使读入与编程两个操作**去耦**，同时也使整个阵列具有更好的耐用性与更低的能耗，FET所具有的栅极可实现对电流，进而实现对单元权重的精确调控。

- **文章创新点：**

  - 使用基于$\text{Li}^+$嵌入$\text{WO}_3$的ECRAM进行神经形态运算，实现了高精度，高速及低功耗的目标。
  - 文中所提出的ECRAM在权重更新方面具有卓越的线性与对称性。

---

#Metal-oxide based, CMOS-compatible ECRAM for Deep Learning Accelerator  
><font face="Times New Roman" >  Kim  S, Todorov T, Onen M, et al. Metal-oxide based, CMOS-compatible ECRAM for deep  learning accelerator[C]//2019 IEEE International Electron Devices Meeting  (IEDM). IEEE, 2019: 35.7. 1-35.7. 4.  </font>

---

- **写作目的：**

  本文主要介绍一种基于金属氧化物结构的电化学存储器（MO-ECRAM），在展示其高速、低功耗、对称开关特性等优异性能的同时，首次通过实验演示了并行阵列操作、随机更新方案和零偏移技术。

- **内容记录：**

  - MO-ECRAM对称的开关特性：

  ![image-20220825094045643](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094045643.png)

  - 分别以不同脉宽的脉冲测定其开关特性：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_1.png" alt="蜂蜜浏览器_1" style="zoom: 50%;" />

    分别在10$\mu s$/1$\mu s$/100$ns$/10$ns$的条件下测定其开关特性，脉宽越窄，最终运算速度越快，但相对应的对称性与开关比均会降低（因为单位脉冲变化的$\Delta G$会变小），但MO-ECRAM在10$\mu s$-10$ns$的范围内均显示出可观的开关特性。

  - 单位脉冲对应的电导更新值随脉宽、电压脉冲幅度、电流脉冲幅度的变化：

  ![image-20220825094406166](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094406166.png)

  - 使用阵列演示顺序编程与并行编程，展示各单元间具有良好的独立性：

  ![image-20220825094426529](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094426529.png)

  - 使用随机更新方案和零偏移技术进行阵列演示，零偏移技术可参考文献：

    > <font face="Times New Roman" >Kim et al., arXiv:1907.10228, (2019).  </font>

- **批注：**

  - 以下是基于$\text{Li}^+$的ECRAM的开关特性：

    ![image-20220825094600546](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094600546.png)

    与MO-ECRAM对比，基于$\text{Li}^+$的ECRAM在编程与读取的交界处电导有明显的跃迁现象，可能与$\text{Li}^+$本身是否运动有关，值得研究。

  - 各单元间的读写之所以具有良好的独立性，是因为该阵列可选用电压脉冲进行读写，而电压脉冲与$\Delta G$呈指数关系，因此单元间较小的潜行电流对$\Delta G$的干扰相较编程电流本身会非常小。

- **文章创新点：**

  - 提出了MO-ECRAM这一具有良好性能的存算一体阵列单元。
  - 分别测定了电压脉冲与电流脉冲对$\Delta G$的调控，利用电压脉冲幅度与$\Delta G$的指数关系减小单元间编程的干扰。
  - 使用随机更新方案和零偏移技术进行阵列演示。

---

# Capacitor-based Cross-point Array for Analog Neural Network with Record Symmetry and Linearity  

><font face="Times New Roman" >  Li Y, Kim S, Sun X, et al. Capacitor-based cross-point array for analog neural network with record symmetry and linearity[C]//2018 IEEE Symposium on VLSI Technology. IEEE, 2018: 25-26. </font>

---

- **写作目的：**

  本文主要介绍一种基于电容器的cross-point阵列，可以实现目前最优的线性度与对称性，同时还讨论了在该阵列上应用**低泄漏DRAM**（low-leakage DRAM）技术的可能性。

- **内容记录：**

  - 基于电容器的阵列单元设计：

    ![image-20220825095228252](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095228252.png)

    电流源左方的反相器为1个数字反相器+2个模拟反相器，数字反相器，模拟反相器的作用主要是利用XW_P与XW_N对输入差模信号VGP与VGN进行调制，进而调制电流源的电流输入。

  - cross-point阵列的构造：

  ![image-20220825095304316](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095304316.png)

  - 对阵列单元编程并行性的测试（也可以说是对各单元间独立性的测试）：

    ![image-20220825095330362](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095330362.png)

    读图可知，2$\times$2阵列中，各单元的权重更新值$\Delta V$在并行编程时保持独立与线性。

  - 对电容保持时间的测试：

    ![image-20220825095413594](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095413594.png)

    保持时间的量级为1s，因此如果权重更新所经历的时间量级小于保持时间，那么在权重更新过程中便无需进行单元刷新。

- **批注：**

  - 基于电容器设计的阵列单元的优点：相较于基于NVM设计的阵列单元，电容器单元在权重更新时具有更高的精度，同时使用电容器单元的阵列在NN训练中也不需要进行定时刷新，因为单元权重在训练期间本身会不断更新。这解决了电容器单元阵列存储信息具有易失性的缺陷。

- **文章创新点：**

  - 设计了一种基于电容器的cross-point阵列，在开关特性上可以实现目前最优的线性度与对称性。
  - 利用该阵列高速读写的特性，使电容器在NN训练中无需进行刷新，巧妙避开了利用电容器存储权重信息易失的缺陷。

---

#Experimental Demonstration of Non-volatile Capacitive Crossbar Array for In-memory Computing 

><font face="Times New Roman" >  Luo Y C, Hur J, Wang T H, et al. Experimental demonstration of non-volatile capacitive crossbar array for in-memory computing[C]//2021 IEEE International Electron Devices Meeting (IEDM). IEEE, 2021: 1-4.</font>

---

- **写作目的：**

  本文通过实验演示了基于铁电材料$\text{Hf}_{0.5}\text{Zr}_{0.5}\text{O}_2$的电容式cross-point阵列在内存运算方面的应用。

- **内容记录：**

  - $\text{TiN/HZO/TiN}$电容器cross-point阵列的制作过程：

    ![image-20220825095900810](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095900810.png)

    使用**等离子体增强原子层沉积技术（plasma-enhanced atomic layer deposition, PEALD）**进行器件制作。

  - 电容式cross-point阵列与传统1T1R阵列的对比：

    ![image-20220825095947176](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095947176.png)

    1. 1T1R式同时具备静态与动态功耗（因其阵列是导通的，会存在静态电流），电容式仅具有动态功耗。
    2. 1T1R式的开关比较小，而电容式的则较大。
    3. 1T1R式较难进行3D堆叠，而电容式进行3D堆叠的可能性较大。

  - 1/3 $V_\text{w}$写入方案下可能引发的误差：

    ![image-20220825100059698](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825100059698.png)

    造成误差的主要原因是，在这种编程方案下，除被选中的单元外，其余的一些单元也会存在较小的电势差，这可能会引发错误，但按本文中的实验，所引发的错误率均在方案所设置的裕度内。

- **批注：**

  - **BEOL**与**FEOL**：
    - **BEOL（back end of line）**是IC制造的第二部分，其中各个器件（晶体管，电容器，电阻器等）与晶圆上的布线（金属化层）互连。
    - **FEOL（front end of line）**是IC制造的第一部分，其中各个组件（晶体管，电容器，电阻器等）在半导体中图案化。

---

# Nanosecond protonic programmable resistors for analog deep learning  

><font face="Times New Roman" >Onen M, Emond N, Wang B, et al. Nanosecond protonic programmable resistors for analog deep learning[J]. Science, 2022, 377(6605): 539-543.</font>

---

- **写作目的：**

  本文主要介绍一种可用于实现模拟DNN的质子可编程电阻（protonic programmable resistor），在具有良好的对称性与线性的同时能达到纳秒级的编程速度。并基于此器件讨论基于固态离子的ECRAM用于模拟人工突触的速度极限。

- **内容记录：**

  - **为什么要选择固态离子器件模拟人工突触**：水溶液中的离子只能实现毫秒级的反应速度，这并非是离子本身的限制，而是由于为使离子的速度更快，必然需要更大的外部电压，而液态水在高电压下会分解，从而从根本上限制了离子的速度上限。
  - 提升器件编程速度的两大主要方向：**尽可能高的外部电压**和**尽可能小的器件尺寸**，高电压提升的是器件内粒子的驱动力，小器件尺寸缩小的是粒子的运动距离。
  - 本文设计的质子可编程电阻的结构及TEM图像：

  ![image-20220825100545730](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825100545730.png)

  ​		采用$\text{Pd}$作为栅控材料，$\text{WO}_3$作为导电通道，纳米多孔PSG（无机磷硅酸盐玻璃）作为质子SE。

  - 质子可编程电阻表现出的高速与低能耗的编程特性：

  ![image-20220825100700793](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825100700793.png)

  - 该器件的转移特性（栅控特性）：
    $$
    I_G(V_\text{pulse})\propto\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$
    由此得出的关系式：
    $$
    \Delta G=kt_\text{pulse}^\beta\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$

  - 在长脉宽脉冲作用下器件可能会退化，主要是由于$\text{PSG}-\text{WO}_3$界面会有太多高能质子聚集，并可能产生$\text{H}_2$：

  ![image-20220825101047794](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825101047794.png)

- **批注：**

  - 用于模拟DNN的器件对**权重保持耐久性**与**状态切换精确性**的权衡：应当优先考虑状态切换时的精确性，因为在DNN的训练中，权重实际上是在不断更新的，我们实际上只需保证权重能够保持至下一次权重更新时即可，而无需对其进行太长时间的保存。NN训练的目的并非为了记住训练集，而是为从训练集中获取分类的依据，分类的精确性取决于对权重调整的精确性，而非记忆的持久性。

  - 解释公式：
    $$
    \Delta G=kt_\text{pulse}^\beta\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$
    由于：
    $$
    I_G(V_\text{pulse})\propto\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$
    可知电导$G$为$I_G$对$V_\text{pulse}$的导数，应当正比与$\cosh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})$，而$\Delta G$则为$G$对时间$t_\text{pulse}$的微分，因此会有上式。
---

# Memory-Logic Hybrid Gate with 3D-Stackable Complementary Latches for FinFET-based Neural Networks  

><font face="Times New Roman" >Lee C, Chih Y D, Chang J, et al. Memory-logic hybrid gate with 3D-stackable complementary latches for FinFET-based neural networks[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 38.7. 1-38.7. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于FinFET调控与RRAM编程的**互补锁存器结构**（complementary latch, CL），研究了其稳定性与耐久性，并基于此对其用于3D堆叠的拓展性进行了讨论。

- **内容记录：**

  - 单层CL的电路原理与真值表：

    ![image-20220825102422635](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102422635.png)

    当S=0，即FinFET关断时，CL处于读状态；当S=1，即FinFET开启时，CL处于写状态。

  - 单层CL的物理结构与TEM图像：

  ![image-20220825102452412](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102452412.png)

  - 物理结构中，Via1与M1及其中部介质构成了$R_1$与$R_2$，M2相当于电路原理图中的$Y$。

  - 对器件间均匀性的测试：

    ![image-20220825102618317](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102618317.png)

    虽然器件与器件间的HRS与LRS状态存在着较大的偏移，但是由于RRAM具有较大的开关比HRS/LRS，因此在CL中由于$R_1$与$R_2$的互补性，输出$Y$并不会有较大偏移：

    ![image-20220825102651173](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102651173.png)

  - 3D堆叠的拓展：

    ![image-20220825102714880](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102714880.png)![image-20220825102719874](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102719874.png)

    其中M5为输出$Y$，Via3与M3构成$R_3$与$R_4$，Via1与M1分别构成$R_1$与$R_2$，$R_5$与$R_6$。

- **批注：**

  - 采用FinFET器件的优势：FinFET器件在抑制亚阈值电流和栅极漏电流方面有着绝对的优势。FinFET的双栅或半环栅等体鳍形结构增加了栅极对沟道的控制面积，使得栅控能力大大增强，从而可以有效抑制短沟效应，减小亚阈值漏电流。

  - 使用镜像结构抑制$R_1$与$R_2$的不对称性：

    ![image-20220825102841274](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102841274.png)

    这类似于差分放大器的设计思路，当某一侧的$R_1$与$R_2$因制造而存在较大差异时，另一侧的$R_1$与$R_2$便会对其进行调制。

- **文章创新点：**

  - 使用FinFET器件与RRAM组成TR结构，具有更好的调控性。
  - 构造**镜像器件**减小因器件自身缺陷产生的误差。
  - 讨论了器件用于3D堆叠的可能性。

---

# 3D RRAMs with Gate-All-Around Stacked Nanosheet Transistors for In-Memory-Computing  

><font face="Times New Roman" >Barraud S, Ezzadeen M, Bosch D, et al. 3D RRAMs with gate-all-around stacked nanosheet transistors for in-memory-computing[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 29.5. 1-29.5. 4.</font>

---

- **写作目的：**

  本文主要介绍一种可进行3D堆叠的1T1R RRAM，在介绍其基本结构的同时，利用TCAD仿真对晶体管参数进行优化，最后讨论**SCL（Scouting Logic）**在该结构设计上的可行性。

- **内容记录：**

  - 本文介绍的1T1R RRAM的结构：

    ![image-20220825103228625](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103228625.png)

    通过字线（WL）控制1T的栅极，确定选中单元的$z$坐标；通过源极线（SL）控制1R，确定选中单元的$x$坐标；通过位线（BL）与SL结合控制对单元的读写，同时确定选中单元的$y$坐标。

  - 在制造RRAM时，通过将BL进行金属化，将BL的电阻率降低至原值的$10^{-3}$：

  ![image-20220825103319523](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103319523.png)

  - 使用TCAD仿真对晶体管性能进行优化设计，具体包括：

    1. 对通道掺杂浓度的讨论：

       ![image-20220825103410093](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103410093.png)

       不同掺杂浓度下的转移特性曲线。

       掺杂浓度越高，静电特性越好，但对应的$I_\text{ON}$更大，对应着更大的功耗。

    2. 对导电通道宽度的讨论：

       ![image-20220825103454286](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103454286.png)![image-20220825103459456](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103459456.png)

    导电沟道宽度越宽，对应着更大的功耗，但对较窄的导电沟道，又容易引发**DIBL效应**。

  - 1T1R RRAM实现SCL的原理：

  ![image-20220825103550795](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103550795.png)

- **批注：**

  - **DIBL效应（Drain-induced Barrier Lowering）**：在导电沟道宽度较小时，可能会引发因源漏区过于靠近而引发沟道势垒的下降，从而导致漏电的增加，同时降低Vth：

  ![image-20220825103617638](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103617638.png)

  - **SCL（Scouting Logic）**：中文直译为侦察逻辑，一种新型逻辑设计，通过对忆阻器阵列的读取，利用基尔霍夫定律与电流比较器实现任意逻辑门的功能，右图展示了AND门与OR门的实现方法。

- **文章创新点：**

  - 设计了可用于3D堆叠的1T1R RRAM结构。
  - 使用TCAD对晶体管参数进行优化，节约实际实验测试的成本。
  - 探究了基于1T1R RRAM实现SCL的可行性。同时在SCL中采用**DC（双编码）**，能取得相对**SC（单编码）**2倍的能效。

---

# Monolithic 3D Integration of High Endurance Multi-Bit Ferroelectric FET for Accelerating Compute-In-Memory  
><font face="Times New Roman" >Dutta S, Ye H, Chakraborty W, et al. Monolithic 3D integration of high endurance multi-bit ferroelectric FET for accelerating compute-in-memory[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.4. 1-36.4. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于FeFET的3D-CIM架构设计，对其制造工艺进行了详细描述，同时对其制造工艺的条件对最终器件性能的影响做了讨论，最后讨论了该CIM架构在实际运算时的性能。

- **内容记录：**

  - 传统CIM架构与**Monolithic 3D（M3D）** CIM架构的对比：

    ![](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104222143.png)

    传统的CIM架构将NVM器件单元与外围电路共同安排于FEOL中，而M3D CIM架构将NVM器件单元安排于BEOL中（3D），同时在能耗、面积方面相对传统CIM架构具有显著的优势。

  - 本文设计的1T1FeFET单元：

    ![image-20220825104353235](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104353235.png)

    其中FeFET作为NVM单元实现存储功能，位于上层，通过BEOL工序实现，晶体管（1T）作为调控单元位于下层，通过FEOL工序实现。

  - 1FeFET1T器件的制造工序：

  ![image-20220825104426455](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104426455.png)

  - 使用ALD沉积HfO2后，对退火条件进行改变，考虑不同退火条件下器件性能的变化：

  ![image-20220825104443716](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104443716.png)

- **批注：**

  - 对FeFET来说，由于其采用铁电材料，其不像RRAM，开关特性由I-V曲线进行描述，而一般会由该铁电材料的**极化回线**（P-E loop）给出：

  ![image-20220825104503592](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104503592.png)

- **文章创新点：**

  - 设计并实现了Monolithic 3D（M3D） CIM架构，具有高密度，低能耗的特点。
  - 对器件制作工艺中的条件进行讨论，探究了制作条件对器件性能的影响。

---

# Monolithic 3D Integration of Logic, Memory and Computing-In-Memory for One-Shot Learning  
><font face="Times New Roman" >  Li Y, Tang J, Gao B, et al.  Monolithic 3D Integration of Logic, Memory and Computing-In-Memory for  One-Shot Learning[C]//2021 IEEE International Electron Devices Meeting  (IEDM). IEEE, 2021: 21.5. 1-21.5. 4.  </font>

---

- **写作目的：**

  本文主要介绍一种可用于**一次学习（One-Shot Learning）**的M3D CIM架构，分别介绍了该架构的制造工艺以及最终的设备特性，最后，使用该架构实现了一次学习，实现了高准确率、高速与低能耗。

- **内容记录：**

  - 本文设计的M3D CIM架构的基本结构与制作工艺：

    ![image-20220825104811471](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104811471.png)

    第一层为实现控制逻辑的CMOS电路，在FEOL中进行制造；第二层为基于$\text{HfAlO}_\text{x}$的1T1R阵列，在BEOL中进行制造；第三层为基于$\text{Ta}_2\text{O}_5$的2T2R阵列，在BEOL中进行制造。

  - 该M3D CIM架构中，第一层为基于$\text{Si}$的MOSFET，主要用于实现一些控制逻辑，同时作为数据输入的端口，第二层为RRAM，实现了具有2个卷积层与2个全连接层的CNN，第三层为**TCAM（Ternary Content Addressable Memory）**层，存储CNN中提取的特征并实现查找功能。

  - 探究制造第三层时是否会对第二层的器件特性产生影响：

  ![image-20220825105000953](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825105000953.png)

  ​		读图可知，在第三层制造前后，第二层的开关特性并未显著改变，表明了两层制造工艺的独立		性。

  - M3D CIM实现一次学习的示意图：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825105036584.png" alt="image-20220825105036584" style="zoom:150%;" />

- **批注：**

  - 第三层所选取的2T为**碳纳米管FET（CNTFET）**，它以碳纳米管（CNT）作为导电沟道。
  - **对于制造第二层RRAM是否会对第一层CMOS电路有影响**：由于两者分属BEOL与FEOL，而本文中BEOL采用低温工艺，不会对FEOL中生成的层产生影响。

- **文章创新点：**

  - 设计并实现了一种可用于一次学习的M3D CIM架构，相对于传统GPU能够实现高准确率、高速与低能耗。
  - 在制造工艺上，三层的制造互不影响，相互独立，器件特性得以保存。

---

# SOT-MRAM based Analog in-Memory Computing for DNN inference  

><font face="Times New Roman" >Doevenspeck J, Garello K, Verhoef B, et al. SOT-MRAM based analog in-memory computing for DNN inference[C]//2020 IEEE Symposium on VLSI Technology. IEEE, 2020: 1-2.</font>

---

- **写作目的：**

  本文主要介绍一种可用于实现量化DNN权重存储的SOT-MRAM器件，并通过实验证明其用于实现**模拟内存计算（AiMC）**的合理性。

- **内容记录：**

  - DNN中层间发生的MVM运算在cross-point阵列上的映射：

  ![image-20220825150611130](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825150611130.png)

  - SOT-MRAM单元的读写原理：

    ![image-20220825150638526](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825150638526.png)

    相比STT-RRAM，SOT-MRAM器件的特点是通过在相邻的SOT层中注入面内电流来完成自由磁层的切换，这与STT-MRAM不同，STT-MRAM的电流垂直注入磁隧道结中，读写操作通过同一路径执行：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825150657510.png" alt="image-20220825150657510" style="zoom:150%;" />

  - 实验设计的用于实现三元量化权重（1，0，-1）的**差分电导对**及其量化过程：

    ![image-20220825150726951](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825150726951.png)![image-20220825150734997](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825150734997.png)

    量化时主要是将原权重的分布（PDF）量化为以0，1，-1为中心的分布的叠加，并分别为其分配方差$\sigma_{\text{w,train}}$，其中方差与SOT MRAM电导存在以下转换关系：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825150819771.png" alt="image-20220825150819771" style="zoom:150%;" />

  - 在测试时改变量化使用的方差$\sigma$，发现使用更小的方差能得到更高的训练精度：

  ![image-20220825150913036](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825150913036.png)

- **批注：**

  - DNN的量化：在神经网络实现分类任务时，并不需要我们对权重等参数作完全精确的描述，因此，我们常常会对参数进行量化以期使用更少的比特数对参数进行描述，减少冗余的数据存储。
  - MRAM的**CD（Critical Dimension）**：指MRAM器件存在的一个最小尺寸，当器件小于该尺寸时，器件的读写特性便会因小尺寸而退化。
  - 变异系数（$\sigma/\mu$）：相当于对方差的标准化，使得处于不同量级的数据的离散程度具有可比性，文中使用变异系数判断RA处于不同量级是否会对器件与器件间的均匀性产生影响。

- **文章创新点：**

  - 提出一种可用于实现量化DNN权重存储的SOT-MRAM器件，并从多方面分析其合理性。
  - 在训练与测试中使用了不同的$\sigma$参数，提升了DNN的分类精度。

---

# Multi-pillar SOT-MRAM for Accurate Analog in-Memory DNN Inference  

><font face="Times New Roman" >Doevenspeck J, Garello K, Rao S, et al. Multi-pillar SOT-MRAM for accurate analog in-memory DNN inference[C]//2021 Symposium on VLSI Technology. IEEE, 2021: 1-2.</font>

本文的前置工作：

> <font face="Times New Roman" >Doevenspeck J, Garello K, Verhoef B, et al. SOT-MRAM based analog in-memory computing for DNN inference[C]//2020 IEEE Symposium on VLSI Technology. IEEE, 2020: 1-2.</font>

---

- **写作目的：**

  - 本文主要基于已研究过的，可用于实现**三元权重**量化的SOT-MRAM器件，进一步提出可用于实现**九元权重**量化的SOT-MRAM器件单元，并利用实验展示其良好的量化效果，最后通过DNN训练进行测试。

- **内容记录：**

  - MRAM因其良好的非易失性和可扩展性，是实现DNN权重存储的一个可能方案，但是单个MRAM器件只能实现2个电导水平，表示1bit信息。

  - 使用2个MRAM组合可构成**差分电导对（differential conductance pair）**，实现三元权重（0，-1，1）的表示，但三元权重无法准确表示浮点数，从而导致DNN最终的分类精度下降：

    ![image-20220825151601986](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825151601986.png)

    如图所示，权重表示至少需要9个离散水平才能保证DNN的分类精度。

  - 能够实现5个电导水平的SOT-MRAM器件：

    ![image-20220825151633083](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825151633083.png)

    在写操作时，由于施加于每个MJT结构上的电压VVCMA是随该MJT在SOT-track上的位置而线性变化的，因此这4个MJT共会出现：4P，3P/1AP，2P/2AP，1P/3AP，4AP共5种阻态。而由该器件再进一步构成差分电导对，便可得到具有5+5-1=9种阻态的MRAM器件单元。

  - 由于器件本身的非理想性，器件位于什么电导水平本质上为概率事件：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825151745327.png" alt="image-20220825151745327" style="zoom:150%;" />

    该图反映了在不同写入电流时，各电导水平出现的概率，各电导水平的概率密度峰值不重叠，具有较为良好的区分度。

- **批注：**

  - MRAM通过电压改变磁性材料的极化方向，又被称为**VCMA效应（Voltage Control of Magnetic**

    **Anisotropy effect）**。

  - SOT-MRAM的优势：**高耐久性**，**高速**以及**低功耗**，并具有**良好的扩展性**，同时，相对STT-MRAM，由于其是三端器件，可实现**读写操作间的去耦**。

  - 影响DNN在RRAM阵列中训练精度的三个因素：**电导水平数量**、**BER**（比特错误率）、**各电导水平识别的裕度**。

- **文章创新点：**

  - 基于先前的工作，提出了可用于实现九元权重的SOT-MRAM器件，同时无需额外的外围电路或阵列。有效解决了DNN中浮点数量化的精度问题。
  - 通过测量MRAM器件各电导水平的概率分布，全面而有效地衡量了器件各电导水平的选择性。

---

# Towards 10000TOPS/W DNN Inference with Analog in-Memory Computing – A Circuit Blueprint, Device Options and Requirements  

><font face="Times New Roman" >Cosemans S, Verhoef B, Doevenspeck J, et al. Towards 10000TOPS/W DNN inference with analog in-memory computing–a circuit blueprint, device options and requirements[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 22.2. 1-22.2. 4.</font>

---

- **写作目的：**

  本文主要提出了一种可用于DNN的矩阵向量乘法器的设计蓝图，其基于AiMC技术且能效可达**10000TOPS/W**，同时还对可能实现该架构的3种器件进行了讨论。

- **内容记录：**

  - AiMC技术所需满足的几个基本点：

    1. 能够适应低精度的运算/权重量化。
    2. 能够适应权重存储的退化以及运算中的错误。
    3. 能在DNN推理中获得较高的精度，或者相对传统器件的能耗、面积与成本有明显的提升。

  - NN训练时对错误的耐受能力：

    ![image-20220825152323311](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825152323311.png)

    在本文中，我们希望实现的架构能够实现$\sigma/\text{range}<10\%$。

  - AiMC架构的一种常见的实现方式：

    ![image-20220825152439717](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825152439717.png)

    该实现方案存在一些问题：

    1. 输入DAC的必须是电流，利用电流幅值进行模拟量转化。
    2. **activation line**与**summation line**上因线电阻引起的电压降将会影响MVM运算的精度。
    3. 由于需要实现高速运算，输出端的集成运放需要很大的增益带宽来适应高频信号。

  - 本文采用的AiMC架构设计：

    ![image-20220825152559248](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825152559248.png)

    与先前设计对比，主要有以下优势：

    1. 直接使用电压进行输入，输入量与电压脉冲成正比，便于调制。
    2. 使用**类电流源器件（current source-like elements, CSE）**作为输出，相对阻性器件（RE）错误率更小。

  - 讨论如何减轻activation line与summation line上因线电阻引起的电压降（**IR drop**），分别通过I，R两个侧面进行讨论：

    ![image-20220825152716595](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825152716595.png)

    可知，我们需要器件电阻适当大，编程电流适当小以减少activation line与summation line上的电压降，同时也可将运算速度控制在适当的范围内。

  - 针对理想器件的能效进行简单估算：

  ![image-20220825152752788](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825152752788.png)

  - 对可用于实现本文提出的AiMC架构的器件的讨论：

    - **IGZO-based 2T1C DRAM**：

      ![image-20220825152908369](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825152908369.png)

      基于电荷的权重存储设计，使用2个晶体管分别实现读写操作。同时为解决漏电流以及读出电流太高的问题，采用**IGZO晶体管**。
    
    - **SOT-MRAM**：
    
      ![image-20220825153015900](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825153015900.png)
    
      具有高阻态，但一方面只有2个电导水平，另一方面开关比较低。
    
    - **PCM**：
    
      ![image-20220825153046380](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825153046380.png)
    
      需要选择器，可能并不适合。
  
- **批注：**

  - **TOPS**：Tera Operations Per Second的缩写，1TOPS代表处理器每秒钟可进行$10^{12}$次操作。TOPS/W即可用于衡量硬件进行某种操作的能效。
  - 实现高性能AiMC设计的关键点：
    1. 高阻值（$>1\text{M}\Omega$）以及小电流的器件单元。
    2. 权重存储的变化范围小。
    3. 与外部电路的工作电压兼容。
    4. 器件单元具有较高的面密度。

- **文章创新点：**

  - 全面而完整地对现阶段常用的两种AiMC架构设计进行了介绍，并指出其存在的优缺点。
  - 使用合理的假设对文中介绍的AiMC架构的能效进行了估算，给出了证明其高能效的有效论据。
  - 对适用于本文AiMC架构的器件设计做了分析与讨论，指出其优缺点与可行性。

---

# Confined PCM-based Analog Synaptic Devices offering Low Resistance-drift and 1000 Programmable States for Deep Learning  

><font face="Times New Roman" >Kim W, Bruce R L, Masuda T, et al. Confined PCM-based analog synaptic devices offering low resistance-drift and 1000 programmable states for deep learning[C]//2019 Symposium on VLSI Technology. IEEE, 2019: T66-T67.</font>

---

- **写作目的：**

  本文主要讨论了一种外加薄金属衬套的PCM器件（**PCM with a thin metallic liner**），具有传统PCM无法实现的高度线性、低电阻漂移、高耐久性的特性。并通过MNIST数据集对其进行测试，体现其在DNN推理应用中的可靠性。

- **内容记录：**

  - 基于文献：

    > <font face="Times New Roman" >Kim W, BrightSky M, Masuda T, et al. ALD-based confined PCM with a metallic liner toward unlimited endurance[C]//2016 IEEE International Electron Devices Meeting (IEDM). IEEE, 2016: 4.2. 1-4.2. 4.</font>

    给出了具有薄金属衬套的PCM器件具有高度线性与高耐久性的原因：

    ![image-20220825153818084](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825153818084.png)

    高度线性主要是因为薄金属衬套相当于一个线性电阻与PCM器件并联，电阻的$I-V$线性关系会对器件整体的编程线性度进行调制；高耐久性则是因为金属衬套会防止编程材料形成空隙。

  - 文中分别选用了3种金属衬套A/B/C，并分别对具有这3种衬套的PCM进行读写测试：

    ![image-20220825153917497](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825153917497.png)![image-20220825153922970](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825153922970.png)

    1. PCM A/B/C均在编程时表现出高度的线性、低噪声以及较小的电阻漂移。
    2. PCM B可实现更高的耐久性，而PCM C可实现更低的电导漂移。
    3. 在**高阻态**与**最低阻态**下，PCM A均表现出较低的电阻漂移与较低的噪声。

  - 可用于实现DNN推理的差分电导对：

  ![image-20220825154035860](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825154035860.png)

- **批注：**

  - **对外加金属衬套的PCM具有高耐久性的进一步解释**：

    本文中提到的PCM是使用**原子层沉积技术（ALD）**沉积**GST材料（$\text{Ge}_2\text{Sb}_2\text{Te}_5$）**制作的，在初始的几次编程时，$\text{Sb}$与$\text{Te}$会向器件两端发生偏析：

    ![image-20220825154229689](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825154229689.png)

    这使得PCM的切换区域逐渐移向中央，而外加的金属衬套会保证材料的致密性，从而防止了$\text{Sb}$与$\text{Te}$的进一步偏析，保证了后续编程的稳定性。

---

# 8-bit Precision In-Memory Multiplication with Projected Phase-Change Memory 

> <font face="Times New Roman" >  Giannopoulos I, Sebastian A, Le  Gallo M, et al. 8-bit precision in-memory multiplication with projected  phase-change memory[C]//2018 IEEE International Electron Devices Meeting  (IEDM). IEEE, 2018: 27.7. 1-27.7. 4.  </font>

---

- **写作目的：**

  本文主要介绍一种能够实现高精度乘法运算的**Proj-PCM**器件，同时在读写时具备较小的电导漂移与较低的噪声，文中同时提出了针对温度引发电导漂移的补偿方案，并最终实验演示了一个基于神经网络的图像分类任务。

- **内容记录：**

  - 外加投影层的Proj-PCM器件，及其电导的动态范围：

  ![image-20220825155008068](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155008068.png)

  ![image-20220825155014669](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155014669.png)

  - Proj-PCM相对传统PCM具有：

    1. 在读取时电导值具有较低的场依赖性，即电导基本不会随施加的读取电压变化。
    2. 更高的耐久性，电导水平能在更长时间内维持不变。
    3. 更低的编程噪声。
    4. 温度引发的电导漂移更少，电导漂移与温度间具有更好的量化关系，便于在后续工作中对温度影响进行补偿。

    ![image-20220825155138710](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155138710.png)![image-20220825155143668](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155143668.png)![image-20220825155201024](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155201024.png)![image-20220825155213009](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155213009.png)

  - 使用单个Proj-PCM器件实现标量乘法，能够达到8位精度。

  - Proj-PCM电导水平随温度的漂移可使用简单的公式表达：

    ![image-20220825155258506](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155258506.png)

    在本文中仅考虑投影层的温度效应，而$G_p(T)$中的系数$\alpha_p$是一个独立于电导状态与温度的常量，因此可较好地设计补偿方案如下：

    ![image-20220825155332594](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825155332594.png)

- **批注：**

  - 本文实质上利用Proj-PCM提出了CIM技术运算低精度的一种解决方案。本文提出的方案是基于**器件级别（device-level）**的，相对应地，还可以在**架构级别**与**系统级别**提出相应的运算精度优化方案。
  - 探究PCM电导水平的场依赖性是有必要的，因为PCM是二端器件，其读写是通过同一路径的，因此读取操作时的低场是否会影响电导水平是必须要考虑的因素。

- **文章创新点：**

  - 提出一种能够实现高精度乘法运算的Proj-PCM器件，同时在读写时具备较小的电导漂移与较低的噪声。
  - 针对传统PCM与Proj-PCM进行性能对比，体现Proj-PCM的优势。
  - 针对温度引起的PCM电导漂移设计了补偿方案。
  - 分别对单个器件实现的标量乘法与多个器件组成的阵列实现的分类任务的精度进行了测试，较为全面。

---

# A no-verification Multi-Level-Cell (MLC) operation in Cross-Point OTS-PCM  

> <font face="Times New Roman" >  Gong N, Chien W, Chou Y, et al. A no-verification multi-level-cell (mlc) operation in cross-point ots-pcm[C]//2020 IEEE Symposium on VLSI Technology. IEEE, 2020: 1-2.  </font>

---

- **写作目的：**

  本文主要介绍一种基于OTS-PCM的MLC实现方案，并系统讨论了“1/2V”方案下的MLC操作，同时对读写过程中的**阈值电压漂移现象**进行了简要讨论。

- **内容记录：**

  - 基于OTS-PCM的架构设计及其进行3D堆叠后的效果：

  ![image-20220901213754879](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901213754879.png)![image-20220901213810472](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901213810472.png)

  - 可见在进行3D堆叠后，每条字线（WL）与位线（BL）其实都是被2层阵列所共用的。

  - 对SET电压的幅值与脉宽的调试：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901213842063.png" alt="image-20220901213842063" style="zoom:150%;" />

    可见，当设置时间小于300ns时，99%的阵列单元可被SET成功。

  - 对OTS-PCM阵列耐久性的测试，当经过$10^9$个周期循环后，PCM的SET电压$V_\text{tS}$与RESET电压$V_\text{tR}$基本保持不变：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901214001194.png" alt="image-20220901214001194" style="zoom:150%;" />

  - 文章讨论的两种读取方案（**DC方案**与**AC方案**）：

    ![image-20220901214042166](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901214042166.png)

    **DC方案**即是使用离散化的脉冲进行SET与RESET，每个脉冲的脉宽在毫秒级；**AC方案**即是使用连续变化的斜变波形进行SET与RESET，可实现小于毫秒级的反应速度。

  - $V_\text{tR}$会随AC方案中SET/RESET时间的减小而增大，这可以使用OTS的**丝状开关机制（filamentary switching）**进行解释：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901214139907.png" alt="image-20220901214139907" style="zoom:150%;" />

  - 文章讨论的两种编程方案：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901214212407.png" alt="image-20220901214212407" style="zoom:150%;" />

    - **partial-SET方案：**首先使用一个恒定幅值的$V\_\text{pgm}$脉冲进行RESET，其次对SET时间进行调制。
    - **partial-RESET方案：**首先单元需保持在SET状态，其次通过不同幅值的$V\_\text{pgm}$脉冲进行RESET。

  - partial-SET方案与partial-RESET方案的效果对比：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901214357121.png" alt="image-20220901214357121" style="zoom:150%;" />

    在测试效果时，为保证严谨性，使用了**开环编程（open-loop programming）**，即不会对写入的状态进行检测并重新写入（**read-verify-rewrite**），而实际应用时可以采取该种方案确保编程的准确性。

  - 对OTS开关阈值电压$V_\text{t}$漂移的探究及曲线关系拟合：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901214453903.png" alt="image-20220901214453903" style="zoom:150%;" />

- **批注：**

  - 有关本文使用的**1/2V编程方案**：

    基于文献：

    > <font face="Times New Roman" >Chen Y C, Chen C F, Chen C T, et al. An access-transistor-free (0T/1R) non-volatile resistance random access memory (RRAM) using a novel threshold switching, self-rectifying chalcogenide device[C]//IEEE International Electron Devices Meeting 2003. IEEE, 2003: 37.4. 1-37.4. 4.</font>

    给出了1/2V编程方案的具体描述：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901214709069.png" alt="image-20220901214709069" style="zoom:150%;" />

    在编程时，对选中的单元所在字线施加V电压，其余字线施加1/2V电压；对选中单元位线施加0电压，其余位线施加1/2V电压。相对应地，还有1/3V方案，可以在读写时实现更低的编程电流以及更大的读取裕度：

    ![fig1](C:/Users/86181/Desktop/%E4%B8%AA%E4%BA%BA%E8%B5%84%E6%96%99/TIME/Meetings/Art8/fig1.png)

  - 1/2V读取方案的成功取决于读取的$V_\text{tr}$的大小，应当介于最低读取电压与最低编程电压之间：

  ![fig2](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig2.png)

- **文章创新点：**

  - 给出一种基于OTS-PCM的MLC实现方案，并系统讨论了1/2V方案下的MLC操作。
  - 对PCM阵列的读写操作分别给出了DC/AC，partial-SET/RESET的实现方案并予以讨论。
  - 分析了OTS开关阈值电压漂移的现象。

---

# An Access-Transistor-Free (OT/lR) Non-Volatile Resistance Random Access Memory (RRAM) Using a Novel Threshold Switching, Self-Rectifying Chalcogenide Device  

> <font face="Times New Roman" >Chen Y C, Chen C F, Chen C T, et al. An access-transistor-free (0T/1R) non-volatile resistance random access memory (RRAM) using a novel threshold switching, self-rectifying chalcogenide device[C]//IEEE International Electron Devices Meeting 2003. IEEE, 2003: 37.4. 1-37.4. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于**硫属元素化物**（chalcogenide）的RRAM阵列设计，该阵列采用无存取晶体管的设计（**0T1R, Access-Transistor-Free**），文章同时对器件特性、阵列特性与读写方案进行了讨论。

- **内容记录：**

  - **TF-RRAM（Transistor-Free RRAM）**的开关特性：

    ![image-20220901215437586](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215437586.png)

    TF-RRAM的器件单元结构为$\text{TiW}$-$\text{GST}$材料-$\text{W}$，由于硫属元素化物材料总是包含非晶相成分，因此不会表现出在传统PCM器件中处于晶相时的欧姆特性。

  - TF-RRAM器件的读写脉冲：

    ![image-20220901215538289](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215538289.png)

    编程脉冲有较大的脉宽，且SET与RESET的电压幅值均大于$\text{High}\ V_\text{th}$，读取脉冲脉宽较小且电压幅值介于$\text{High}\ V_\text{th}$与$\text{Low}\ V_\text{th}$之间，因此不会导致器件发生状态切换。

  - 存储器的阵列设计，讨论了1/2V与1/3V两种读取方案：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215708042.png" alt="image-20220901215708042" style="zoom:150%;" />

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215722322.png" alt="image-20220901215722322" style="zoom:150%;" /><img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215727558.png" alt="image-20220901215727558" style="zoom:150%;" />

    1/2V方案有较小的读取电流，1/3V方案有较大的读取裕度与较小的编程电流。

  - 对器件编程脉冲的脉宽与幅值、$V_\text{th}$随编程脉冲幅值的变化，$V_\text{th}$在读写操作下的保持特性，$V_\text{th}$的耐久性进行了探究：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215833350.png" alt="image-20220901215833350" style="zoom:200%;" /><img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215853011.png" alt="image-20220901215853011" style="zoom:200%;" /><img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215917900.png" alt="image-20220901215917900" style="zoom:200%;" /><img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215930068.png" alt="image-20220901215930068" style="zoom:200%;" /><img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901215943039.png" alt="image-20220901215943039" style="zoom:200%;" />

- **批注：**

  - 标准尺寸的MOSFET所提供的电流无法实现传统PCM器件的晶相与非晶相之间的转换，因此传统的PCM器件若要使用MOSFET作为存取晶体管/选择器，则器件尺寸需要相应地放大。

  - **为什么TF-RRAM可以不使用存取晶体管？**

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901220043751.png" alt="image-20220901220043751" style="zoom:200%;" />

    如上图，传统PCM器件在晶相会表现出欧姆特性，自身无法实现整流（**Self-Rectify**），而对TF-RRAM，由于硫属元素化物材料总是包含非晶相成分因此总可以实现整流，因此无需外加存取晶体管辅助整流。

    另外，由于TF-RRAM的这种特性（及其**较小的亚阈区电流**与**较大的开关比**），该器件也常用于整流。

- **文章创新点：**

  - 给出了一种无需存取晶体管的TF-RRAM设计。
  - 对器件/阵列特性进行全面分析。

---

#MLC PCM Techniques to Improve Nerual Network Inference Retention Time by $10^5$X and Reduce Accuracy Degradation by 10.8X  

> <font face="Times New Roman" >Khwa W S, Akarvardar K, Chen Y S, et al. MLC PCM Techniques to Improve Nerual Network Inference Retention Time by 105X and Reduce Accuracy Degradation by 10.8 X[C]//2021 Symposium on VLSI Technology. IEEE, 2021: 1-2.</font>

---

- **写作目的：**

  本文主要介绍了3种用于优化MLC PCM的方案，以解决MLC PCM在神经网络应用中所面对的挑战。

- **内容记录：**

  - PCM可选择的两种MLC方案：

    ![image-20220901220353368](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901220353368.png)

    第一种方案是对PCM的MLC状态完全精确的描述，即各状态间不存在重叠，这种方案不存在信息缺失，但对设备的要求很高；第二种方案是对PCM的MLC状态有重叠地描述，这种方案可实现更高密度的存储，但会有一定的信息缺失。

  - 研究发现，重叠的 MLC 状态可以被神经网络的容错特性所容忍。

  - MLC PCM在神经网络应用中所面临的3个挑战：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig3.jpg" alt="蜂蜜浏览器_fig3" style="zoom:80%;" />

    1. 对不同设备性能需求的不平衡。
    2. 不同MLC状态的出现概率不均匀。
    3. 不同MLC状态的保持特性不同。

  - 表示不同位数的MLC状态的误码率会对NN的精度有不同的影响：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901220635753.png" alt="image-20220901220635753" style="zoom:150%;" /><img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901220642119.png" alt="image-20220901220642119" style="zoom:150%;" />

    整体来说，处于低位的状态发生误码，对权重整体的数值影响不大，因此对NN的精度影响较小，处于高位的状态发生误码，对权重的数值影响较大，因此对NN的精度影响较大。

  - 为解决MLC PCM在NN应用中的挑战，所提出的3个解决方案：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901220727171.png" alt="image-20220901220727171" style="zoom:150%;" />

    1. **DRB：**将高位与低位相互配对，使用一个PCM器件进行表示，降低对每个PCM器件误码率的限制。
    2. **PMR：**通过统计高位（W[6]与W[7]）二进制组合出现的概率，自行对器件的状态进行修正。
    3. **BPP：**通过调整MLC的状态分布，使高位具有更大的读取裕度，从而降低高位的误码率（BER）。

- **批注：**

  - 对PMR的进一步说明：
    PMR指通过统计高位（W[6]与W[7]）二进制组合出现的概率，自行对器件的状态进行修正。在本文中，W[6]=W[7]的概率高达94.28%，因此可通过W[6]的状态对W[7]的状态进行修正，以降低W[7]的BER。
  - 相对而言，在传统方案中，由于描述高位的PCM器件发生误码后对权重数值的影响大，因此对该PCM器件BER的要求更为严格。

- **文章创新点：**

  - 针对MLC PCM在NN应用中的挑战进行了较为全面的分析。
  - 为解决MLC PCM在NN应用中的挑战，分别提出了DBR、PMR、BPP共3个解决方案。


---

# Characterizing Endurance Degradation of Incremental Switching in Analog RRAM for Neuromorphic Systems  
> <font face="Times New Roman" >Zhao M, Wu H, Gao B, et al. Characterizing endurance degradation of incremental switching in analog RRAM for neuromorphic systems[C]//2018 IEEE International Electron Devices Meeting (IEDM). IEEE, 2018: 20.2. 1-20.2. 4.</font>

---

- **写作目的：**

  本文主要介绍了一种用于测试模拟RRAM**耐久性（endurance）**的测试平台，并基于该平台对模拟RRAM的耐久性进行了较为全面的研究与表征。

- **内容记录：**

  - 部分NN推理任务对RRAM阵列的耐久性需求：

    ![image-20220901221223691](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221223691.png)

    通常，**用于数据存储**的RRAM的耐久性在$10^5-10^7$个循环左右，但通过**弱编程脉冲**实现模拟权重的**增量更新（incremental switching）**，可以提升RRAM的耐久性。

  - 表征模拟RRAM耐久性的挑战：

    1. 难以控制RRAM在指定的电阻窗口内发生模拟切换。
    2. 缺少有效的耐久性衡量标准。
    3. 测试的时间问题，统计与测量需要较长时间。

  - 使RRAM在指定电阻窗口内发生模拟切换的解决方法：使用**可变电压脉冲**对RRAM单元进行SET/RESET，并在每个循环后对编程脉冲的幅值进行**反馈修正**：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig4.jpg" alt="蜂蜜浏览器_fig4" style="zoom:80%;" />

    每次编程结束后，观察RRAM阻态是否落在电阻窗口内，若不是，则通过修正源/漏极电压来修正编程脉冲。

  - 在能够控制电阻窗口后，对不同电阻窗口对应的耐久性进行测试：

    ![image-20220901221545786](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221545786.png)![image-20220901221550632](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221550632.png)![image-20220901221605901](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221605901.png)![image-20220901221611255](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221611255.png)

    1. 不同大小的电阻窗口，小电阻窗口的耐久性更优。
    2. 固定LRS，HRS越大，耐久性越差。
    3. 固定HRS，LRS的变化与耐久性基本无关。（与2结合可知HRS对耐久性的影响更大）

  - 因此，为获得更好的编程耐久性，在编程时应选用**电阻水平较小、较窄的电阻窗口**进行编程。

  - 对**HRS对耐久性的影响更大**的解释：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221753969.png" alt="image-20220901221753969" style="zoom:150%;" />

    当RRAM处于HRS（使用**full window**进行编程）时，电场集中于一个很小的间隙区域（gap），因此会对RRAM的材料特性造成较为严重的损害，降低其耐久性。而处于其他状态的RRAM电场分布则较为均匀。

  - 使用弱编程脉冲进行模拟RRAM编程时，耐久性可提升至$10^{11}$以上：

    ![image-20220901221849238](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221849238.png)

    但我们不能只关注RRAM的耐久性，在NN应用中，RRAM实现权重更新的对称性与线性也会随编程周期数的增加而退化：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221909545.png" alt="image-20220901221909545" style="zoom:150%;" />

    当编程周期数大于$10^7$时，权重更新的线性与对称性均有较为明显的退化，此时虽然仍可用于NN训练，但对应的训练精度会下降。

  - RRAM耐久性下降对NN精度的影响：

    ![image-20220901221946216](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901221946216.png)

    **低电阻，小窗口**是NN训练的最佳条件，因其具有**最高的准确性**与**最长的耐久时间**。

  - 新定义**累积电导（accumulated $\Delta G$）**的概念来标准模拟RRAM的耐久性：

    ![image-20220901222125001](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220901222125001.png)

    累积电导指在一次NN训练过程中，每次模拟权重更新时电导增量的代数和，一般来说其是均会分布于一个确定的范围内，如果累积电导超出了该范围，则器件很有可能耐久性受到了破坏。

- **批注：**

  - **耐久性（edurance）**通常用器件特性得以维持的最大编程周期数来衡量；**保持特性（retention）**通常用器件在不进行编程时，其状态不发生退化的最大时间来衡量。
  - RRAM在用作存储器件时，为保证存储数据的准确性，通常采用**大电阻窗口（full window）**，并对每个器件使用强电压脉冲进行二进制编程（即只有LRS与HRS），而在用于NN训练时则采用弱电压脉冲的模拟编程。

- **文章创新点：**

  - 设计并制作了用于模拟RRAM耐久性测试的测试平台，并使用该平台实现了对RRAM电阻窗口的控制。
  - 针对不同电阻窗口RRAM的耐久性进行了全面测试，最终确定低电阻，小窗口是模拟RRAM用于NN训练的最佳条件。
  - 提出了累积电导的概念，用于衡量模拟RRAM的耐久性。

---

# Compute-in-Memory with Emerging Nonvolatile-Memories: Challenges and Prospects  

><font face="Times New Roman" >Yu S, Sun X, Peng X, et al. Compute-in-memory with emerging nonvolatile-memories: Challenges and prospects[C]//2020 ieee custom integrated circuits conference (cicc). IEEE, 2020: 1-4.</font>

---

- **写作目的：**

  本文主要介绍了CIM芯片与eNVM的最新进展，以及对各大厂商生产的eNVM芯片的性能分析与比较。同时，文中也重点探讨了eNVM用于机器学习领域所面临的3个重要挑战。

- **内容记录：**

  - GPU是现在用于加速深度学习的主流平台，但对于传统的GPU而言，在实现矩阵向量乘法的MAC运算时，NN权重、输入与输出数据均会在全局缓冲区与MAC阵列中进行移动，因此。为减少数据移动，将MAC运算直接嵌入至内存阵列中是一个十分有吸引力的方案。

  - 现在较为成熟的CIM技术是基于**SRAM**实现的，但有以下不可忽视的缺点：

    1. SRAM本质上是易失性的，有用于保持数据的静态功耗。
    2. SRAM在保持数据时具有不可忽视的泄漏功耗。

    因此，相比SRAM，eNVM在对芯片面积/功耗有更严格限制的场景中，有更好的应用前景。

  - 各大厂商基于eNVM的CIM芯片原型设计：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911205920959.png" alt="image-20220911205920959" style="zoom: 150%;" />

    IBM最先于2015年设计了基于PCM的CIM芯片，但受限于权重更新时的非对称性与漂移，训练精度十分有限（82.9%）。

  - 一个典型的基于eNVM的CIM芯片设计（ASU/GaTech’s RRAM CIM）：

    ![image-20220911210036480](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911210036480.png)

    这种主流设计主要存在下列问题：

    1. **电平转换器**（level shifter）在芯片中占据着不可忽视的空间。
    2. RRAM阵列末尾的ADC占据的空间甚至大于RRAM阵列本身，很难实现良好的间距匹配。
    3. CIM芯片的推理精度仍因非理想因素的存在而有待提高。

  - 基于eNVM的CIM芯片设计所面临的3个重大挑战：

    - **挑战1：器件开态时的低电阻与较高的编程电压。**

      器件处于开态时的低电阻会导致阵列WL/BL上的电压降明显上升，从而导致权重更新的误差增大，最终导致训练/推理的精度下降。

      同时RRAM具有较高的编程电压，编程电压水平显著高于逻辑电平，因此需要外加电平转换器来满足编程所需的电压，这又会占用额外的面积。同时，对不同开态电阻$R_\text{on}$与编程电压$V_\text{w}$的eNVM阵列设计进行仿真：

      ![image-20220911210255076](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911210255076.png)

      提升$R_\text{on}$有助于减少读写能耗，同时对读写延迟的影响较小；降低$V_\text{w}$可以直接降低写入能耗，并通过消除电平转换器来减少读取延迟与芯片面积。

    - **挑战2：ADC的面积占用与功耗。**

      应用于CIM芯片设计的ADC的需求较为特殊，由于神经网络的容错性，一般ADC**不需要很高的精度**，但相对应地，**CIM芯片对ADC面积有严格的限制**，这主要是因为eNVM阵列较为紧凑，如果ADC的面积很大，而每一列又需要于一个ADC相匹配，这将无法实现很好的间距分配。

      对2种ADC（flash-ADC/SAR-ADC）的对比：

      <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911210406437.png" alt="image-20220911210406437" style="zoom:150%;" />

      SAR-ADC相比flash-ADC拥有较小的面积与功耗，但相对却有较高的延迟。

      ADC可使用电流模式/电压模式的比较器进行制作：

      <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911210437310.png" alt="image-20220911210437310" style="zoom:150%;" />

    - **挑战3：模拟运算时的误差。**

      CIM在进行模拟运算时，主要会有以下误差：**不同器件单元间$R_\text{on}$的不均匀**与**ADC的offset error**。

      不同器件单元间Ron的不均匀性可通过**在编程后进行验证校准**解决（iterative write-verify technique），而ADC的offset error可通过修改器件尺寸、在算法层面设计新型算法进行解决。

- **文章创新点：**

  - 对比了基于SRAM与基于eNVM的CIM芯片原型设计的优缺点，指出了其应用场景。
  - 指出了基于eNVM的CIM芯片原型设计所面临的3个重要挑战，并基于这些挑战预测了CIM芯片未来的发展方向。


---

#Experimental Demonstration of Conversion-Based SNNs with 1T1R Mott Neurons for Neuromorphic Inference    

><font face="Times New Roman" >Zhang X, Wang Z, Song W, et al. Experimental demonstration of conversion-based SNNs with 1T1R mott neurons for neuromorphic inference[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 6.7. 1-6.7. 4.</font>

---

- **写作目的：**

  本文主要介绍了一种基于**Mott忆阻器**与1T1R阵列，用于**SNN**推理的CIM芯片，其相对传统的基于晶体管的CIM芯片具有更高的可扩展性与能效，同时也表现出可观的推理精度。

- **内容记录：**

  - 在算法层面上，SNN具有两个显著的限制：

    1. 缺乏有效的训练算法，现有的SNN训练算法基本是通过传统的BP算法进行参数映射得到的。
    2. 缺乏基于脉冲进行表征的训练数据集。

  - 基于Mott忆阻器与1T1R阵列的SNN硬件设计：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911210908594.png" alt="image-20220911210908594" style="zoom:150%;" />

    通过模拟量表征的向量输入RRAM阵列，再通过SL末尾的Mott神经元设计将模拟输入转化为脉冲输出以实现SNN。

  - Mott忆阻器的设计（Si/NbOx/TiN）及其开关特性：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911210942728.png" alt="image-20220911210942728" style="zoom:200%;" />

  - 对Mott神经元性能的测试：

    ![image-20220911211012727](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211012727.png)![image-20220911211019944](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211019944.png)![image-20220911211025584](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211025584.png)

    三张图分别展示了Mott神经元$V_\text{th}$与$V_\text{hold}$良好的不变性与耐久性，以及器件与器件间的均匀性。

  - 本文中设计的Mott神经元：

    ![image-20220911211115778](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211115778.png)

    器件直接使用寄生电容储存电荷，减少了电容器的使用从而提升了阵列的可扩展性。同时，可通过不同的Input控制MOSFET的沟道电阻，从而使SNN的脉冲频率可变。

  - 可用于多任务处理的X-bar阵列设计：

  ![image-20220911211142058](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211142058.png)

- **批注：**

  - 在本文的设计中，RRAM阵列的输入以及内部的MVM运算仍是模拟量，这有效解决了缺乏基于脉冲进行表征的训练数据集的问题。

  - **TIA**：跨阻放大器（Transimpedance Amplifier），其实就是比例器。

  - 本文中的NN使用的激活函数为$ReLU$，$ReLU(x)=\max{x,0}$，在本文的SNN中，输入为Mott神经元的**栅极电压**，输出为**脉冲频率**。

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211314563.png" alt="image-20220911211314563" style="zoom:150%;" />

    当然，由于Mott材料的切换需发生的一定的电压偏置下，因此本文首先在对Mott忆阻器加入了1.81V的电压偏置。

  - 在多任务处理的X-bar阵列设计中，每一行/多行的多层用于实现一个任务。

- **文章创新点：**

  - 率先通过实验验证了可用于实现SNN推理的硬件设计。
  - 通过使用**Conversion-Based SNN**解决了缺乏脉冲形式数据集的问题。
  - 通过改进Mott神经元设计（利用寄生电容）提升扩展性。


---
#An Artificial Neuron Based on a Threshold Switching Memristor    

><font face="Times New Roman" >Zhang X, Wang W, Liu Q, et al. An artificial neuron based on a threshold switching memristor[J]. IEEE Electron Device Letters, 2017, 39(2): 308-311.</font>

---

- **写作目的：**

  本文主要介绍一种基于**TSM（Threshold Switching Memristor）**材料的人工神经元，可对实际神经元的4种重要特性进行模拟。

- **内容记录：**

  - 基于脉冲神经网络（SNN）的类脑运算因其**较低的能耗**和**与生物神经元的较高相似度**而受到了广泛关注。

  - 现阶段使用CMOS电路设计的人工神经元组成部分太多，无法集成，本文给出一种基于$\text{Ag}/\text{SiO}_2/\text{Au}$的TSM神经元设计。

  - 该神经元属于**IF（integration-and-fire）**神经元，即通过积累电荷，当电荷积累到一定阈值时，神经元被激活并向后方神经元发送脉冲。

  - 实际神经元与本文设计的TSM神经元的对比：

    ![image-20220911211654678](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211654678.png)

    实际上，对人工神经网络的设计设计两个关键要素：**神经元**（Neuron）与**突触**（Synapse），突触通常通过一个**忆阻器阵列**进行模拟，这模拟的是**Pre-Neuron**与**Post-Neuron**之间两两形成的突触网络，神经元则使用**忆阻器构成的电路**加在忆阻器阵列的末端，模拟突触所连接的神经元。

  - 本文基于TSM忆阻器设计的IF神经元：

    ![image-20220911211738312](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211738312.png)

    神经元的输入为模拟电压脉冲，输出为一定频率的尖峰脉冲（spike），同时，该神经元电路分别具有**充电循环**（CL）与**放电循环**（DL）。

  - TSM神经元的基本工作过程：

    ![image-20220911211811649](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911211811649.png)

    首先，在初始状态，忆阻器处于HRS（$R_\text{H}$），24支路近似于开路，此时输入模拟电压脉冲，给电容$C$进行充电，时间常数为$R_SC$，而在电压脉冲未输入时，电容$C$会放电，放电的时间常数为$(R_\text{H}+R_S)C$，而$(R_\text{H}+R_S)C$远大于$R_SC$，这说明流失一定量的电荷所需的时间远大于积累等量电荷的时间。因此在一系列连续电压脉冲的作用下，$C$会不断被充电，直至结点2的电压能够使忆阻器发生切换，由HRS切换至LRS（$R_\text{L}$）。

    而在忆阻器发生切换后，$R_o$上的电压发生突变，并随电容$C$的放电减小至0，此即在输出端产生一尖峰脉冲。

  - TSM神经元对神经元特性的模拟：

    - SM神经元满足**all-or-none定律**：由于忆阻器切换行为的发生必须要达到一定的阈值电压，且当电压高于阈值电压时，忆阻器的电阻保持不变。
    - TSM神经元能够实现通过阈值电压进行调控的尖峰脉冲输出。
    - TSM神经元具有**不应期**：当忆阻器由HRS切换至LRS时，回路2432发生DL，其时间常数(RL+Ro)Cs是很小的，这就导致此时若存在模拟电压脉冲输入，在C上积累的电荷会迅速通过DL过程流失，从而实现神经元所谓的**不应期**。
    - (1)   神经元输出尖峰脉冲的频率可通过输入电压脉冲的幅值进行调制（**strength-modulated frequency response**）：

    ![image-20220911212108820](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212108820.png)

  - 使用TSM神经元实现一个简单的数字识别系统，证明了其用于实现SNN的可行性：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212142678.png" alt="image-20220911212142678" style="zoom:150%;" />

    该系统的权重矩阵直接通过MATLAB进行训练给出，实际测试的仅仅是该SNN对数字的识别精度：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212157496.png" alt="image-20220911212157496" style="zoom:150%;" />

    最终实验结果表明，SNN能够正确识别数字，但这实际上相当于直接将训练集作为测试集，所以对基于TSM神经元实现的SNN的精度还缺乏进一步的探究。

- **批注：**

  - **all-or-none law**：神经传导的一项基本特性。即当刺激达到神经元的反应阈限时，它便以最大的脉冲振幅加以反应；但刺激强度如达不到某种阈限时，神经元便不发生反应。
  - 对本文中的TSM神经元而言，当结点2的电压低于忆阻器发生切换的阈值电压时，便不会有尖峰脉冲输出，而一旦结点2的电压高于阈值电压，无论高出多少，TSM神经元均输出相同幅值的尖峰脉冲，因为忆阻器的$R_\text{L}$是一个常数。

- **文章创新点：**

  - 设计了一种基于TSM材料的IF神经元，并能仿真生物神经元的若干重要特性。
  - 使用TSM神经元实现一个简单的数字识别系统，证明了其用于实现SNN的可行性。


---
#Fully Memristive SNNs with Temporal Coding for Fast and Low-power Edge Computing  

><font face="Times New Roman" >Zhang X, Wu Z, Lu J, et al. Fully memristive SNNs with temporal coding for fast and low-power edge computing[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 29.6. 1-29.6. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于$\text{NbO}_\text{x}$忆阻器的**LIF神经元**设计，可用于实现基于**时间编码（temporal coding）**的SNN，并最终通过人脸识别任务对设计可行性进行了验证。

- **内容记录：**

  - 基于**时间编码（temporal coding）**的TC SNN与基于**频率编码（rate coding）**的RC SNN的对比：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212625925.png" alt="image-20220911212625925" style="zoom:150%;" />

    RC SNN会使用尖峰脉冲的频率对数据进行编码，这意味着对一个数据的描述涉及对一段较长时间内若干尖峰脉冲出现频率的记录，这会导致**较高的能耗**与**较长的反应时间与推理时间**。而TC SNN采用时间进行编码，本文中使用**单尖峰方案（one-spike scheme）**，在减小能耗的同时也缩短了反应时间，同时由于尖峰较为稀疏，对设备的**耐久性需求**也相应降低：

    ![image-20220911212653672](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212653672.png)

    另外，与先前基于RC SNN的神经元设计对比，本文中的LIF神经元的激活是**电流驱动**的（current-driven），这意味着该神经元无需offset电压，拥有较低的编程电压。

  - 基于$\text{NbO}_\text{x}$的**LIF（leaky integrate-and-fire）神经元**设计及NbOx忆阻器的性能测试：

    ![image-20220911212833684](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212833684.png)![image-20220911212841091](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212841091.png)![image-20220911212848414](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212848414.png)

    分别测试了**器件开关的耐久性**，**阈值电压的耐久性**与**器件与器件间阈值电压的均匀性**。

  - 本文设计的电流驱动的LIF神经元：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911212918274.png" alt="image-20220911212918274" style="zoom:150%;" />

    该神经元是在用于RC SNN的RC neuron的基础上改进得到的，在RC neuron上外加一个D触发器与一个**TG**（传输门），使用电流给电容C充电，当忆阻器发生切换，输出端产生第一个尖峰脉冲后，D触发器同时被尖峰的边沿触发，进一步触发TG，TG相当于一个理想开关，D触发器使TG被开路，从而断开了输入，使神经元处于不应期，同时保证神经元仅有单尖峰脉冲输出。此时电容C开始放电，为进一步加速放电速度，外加了一个nMOSFET辅助放电：

    ![image-20220911213017343](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911213017343.png)

    在未加MOSFET时，放电的时间在30000ns左右，而加入后缩短为15ns左右。

    上图同样给出了电流强度对尖峰的调制，**较大的电流强度有利于缩短神经元的反应时间**。

  - 电流驱动的RC neuron与TC neuron的对比：

    ![image-20220911213107686](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911213107686.png)

    读图可知，TC neuron的工作范围要远大于RC neuron这意味着TC neuron可支持更大的突触阵列。

  - 使用LIF神经元实现人脸识别任务：

    ![image-20220911213139012](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911213139012.png)

    对本文使用的LIF神经元抽象出的数学模型，利用该模型进行SNN的训练。

    ![image-20220911213151737](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220911213151737.png)

    训练后的SNN阵列对5张人脸图像的识别达到了100%的精确度。

- **批注：**

  - **时间编码（temporal coding）**：SNN的时间编码方式有多种，本文中所采用的单尖峰方案（one-spike scheme）应该是通过神经元接收首次脉冲的时刻来对数据进行编码，文献：
  
    > <font face="Times New Roman" >Kheradpisheh S R, Masquelier T. Temporal backpropagation for spiking neural networks with one spike per neuron[J]. International Journal of Neural Systems, 2020, 30(06): 2050027.</font>
  
    对这种方法有更为详细的说明。
  
  - **current-driven**与**voltage-driven**：由于IF/LIF神经元产生尖峰输出的物理机制类似，都是通过忆阻器达阈值电压后发生切换行为，但电压驱动的神经元往往需要先施加一个offset电压将忆阻器的电压抬至阈值附近，而电流驱动则不需要。
  
  - **推理**（inference）与**训练**（training）：用于NN应用的忆阻器阵列一般分两种，一种是仅用于已知任务的推理，即阵列单元的权重已经通过软件训练得出，该阵列只需将已知的权重编程至各器件单元上，执行推理任务即可，另一种则需要支持硬件上的训练工作。

- **文章创新点：**

  - 提出了一种基于$\text{NbO}_\text{x}$忆阻器的LIF神经元设计，可用于实现基于时间编码（temporal coding）的SNN，具有低功耗，高速的特性。
  - 使用设计的SNN阵列进行人脸识别任务，验证设计的可行性。


---