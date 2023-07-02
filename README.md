# SEEL5123-AdvanceMicroprocessor_Milestone4
<h2>Important: Please read the pdf documents for further clarification</h2>
<h2>1. Software/Tools setup </h2>
<p>  In this project, STM32CubeIDE is used as the development environment. Some external libraries are imported for signal processing steps, such as the DSP library. For the hardware, the Nucleo-F446RE board and INMP441 Microphone is used.</p>

<h2>2. Configuration Steps </h2>
<h3>DMA Configuration</h3>

<h3>UASRT2 Configuration</h3>

<h3>I2S2 Configuration</h3>

<h2>3. Steps for firmware development </h2>
<p>
  The first step of firmware development is importing required libraries. This can be done in the software packs section in pinout and configuration. The X-CUBE-ALGOBUILD package has a DSP library, which can be included in the project later.
  
  The second step is to construct i2s data array and recording function. The input button is set to alter the recording flag. When recording is started and the i2s array is fully received, indicated by interrupt HAL_I2S_RxHalfCpltCallback and HAL_I2S_RxCpltCallback, it will be processed and save the data to the output variables.
</p>

<h2>4. Steps for hardware development </h2>
<p>
  We are using Omnidirectional Microphone Module I2S Interface INMP441 MEMS to capture the audio input for our project. In order to configure the microphone with the board, STM32CubeMX is used to set up the microphone. The figure below shows the input pin of the board (in red circle) that is connected to the microphone pin. 

  The Serial Audio Interface (SAI) is a synchronous serial bus interface that is used for connecting digital audio devices. It is the most common means for transferring two channels of audio data across system devices. In this project, the protocol used for transferring digital audio is by using I2S based on the microphone datasheet. It used I2S Philips standard. 
</p>

<p>The SAI B is configured as Master mode which means the SAI provides the timing signals such as bit clock (SCK) and frame synchronization (FS)</p>
<p>Audio mode is set as Master Receive as the board receives the audio input from the microphone.</p>
<p>Direct Access Memory is added to allow the storing of audio input from the peripheral directly into the board's memory.</p>
