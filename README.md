# Speech Recognition System

**Objective**  - The main objective of this study is to build a spoken word recognition system which takes audio recordings of the words as an input and predicts the word accurately. Here, all the audio files are in WAV format. This study involves implementing deep learning algorithms trained on dataset of labelled audio samples to classify and decode spoken words.

**What can be achieved** - Though this study is performed with limited set of spoken words, it can have variety of applications as below when it is further studied with more number of words.
* Spoken word recognition technology enables accessibility for individuals with disabilities, such as those who are visually impaired or have mobility limitations. Voice-controlled interfaces allow users to interact with devices, applications, and services using spoken commands, thereby removing barriers to access and enhancing inclusivity.
* Spoken word recognition enables hands-free operation of devices and systems, which is particularly useful in situations where manual interaction is impractical or unsafe, such as while driving, cooking, or operating machinery. Voice-controlled assistants like Siri, Alexa, and Google Assistant allow users to perform tasks without needing to physically touch a device.
* Spoken word recognition can be used in automated customer service systems, such as interactive voice response (IVR) systems, virtual agents, and chatbots, to handle customer inquiries, provide information, and route calls to the appropriate departments. Speech recognition enhances the efficiency and scalability of customer support operations.

**Dataset**
* The data is in the form of audio clips (.WAV format). It has 65000 long utterances of 30 short words, by thousands of different people. The audio clips were originally collected by Google. 
* There are 20 core command words which were recorded with most speakers saying each of them five times. The core words are: yes, no, up, down, left, right, on, off, stop, go, zero, one, two, three, four, five, six, seven, eight, nine.
* There are 10 auxiliary words which most speakers said only once: bed, bird, cat, dog, happy, house, marvin, sheila, tree, wow.
* Size of the dataset – 1.4 GB
* When the data is presented in the row columnar format, there would be 65000 rows and 2 columns (Audio, Command word) where in each row would represent an audio file and the corresponding command word respectively.
* Link for the dataset - *https://developer.ibm.com/exchanges/data/all/speech-commands/*
* Since the dataset is huge for the computational resources to handle, I have sampled 70% of the data from the original dataset.
* The data is sampled in such a way that 70% data is extracted for each class label ensuring that the data from any class label is not missed.
* So, the effective size of the data that has been used for this study is 0.7*1.4 GB = 0.98 GB
* Here target variable "command word" contains all the command words which are classified into 30 categories. ( yes, no, up, down, left, right, on, off, stop, go, zero, one, two, three, four, five, six, seven, eight, nine, bed, bird, cat, dog, happy, house, marvin, sheila, tree, wow)

**Data Featurization**
* Using Librosa, audio file is featurized into array. This array represents the amplitude of the audio signal at a specific point in time. The essentially represents the digital representation of the audio waveform in the raw format.
* These are further processed to compute the mel-scaled spectrogram of the input audio data where the above raw format is used as an input. Mel-Spectrogram is a type of spectrogram where the frequencies are converted to mel scale, which more closely aligns with human perception of sound.
* The resulting spectrogram is then converted to a logarithmic scale. This enhances the contrast and makes it easier to analyze the spectrogram.
* In a linear scale spectrogram, small variations in amplitude may be overshadowed by larger values, making it challenging to discern fine details, especially in regions with low energy. By using a logarithmic scale, the differences in amplitude are more evenly distributed across the range, enhancing the visibility of both low and high-energy components.

**Modelling**

![image](https://github.com/user-attachments/assets/be79a874-c62f-4ac8-8b0b-34e27a7e42e6)

This model is run with following parameters

* Adam Optimizer
* Initial Learning rate – 0.0001
* Batch Size – 16
* Early Stopping with patience 4
* Reduce LR Plateau with a factor of 0.95 with patience 2

**Results**

![image](https://github.com/user-attachments/assets/59a62470-4207-42f9-8734-304ecc53f4dd)

<table>
  <tr style="background-color: lightgrey;">
    <th>@40th Epoch</th>
    <th>Train Loss</th>
    <th>Test Loss</th>
    <th>Train Accuracy</th>
    <th>Test Accuracy</th>
  </tr>
  <tr>
    <td>Custom LSTM model</td>
    <td>0.1999</td>
    <td>0.5037</td>
    <td>0.9371</td>
    <td>0.8734</td>
  </tr>
</table>

![image](https://github.com/user-attachments/assets/42749c48-9f8f-43a4-8b88-20ef763192eb)

![image](https://github.com/user-attachments/assets/ae372b68-db56-46c1-a934-7de9e058e09e)

**Deployment**

The application has beeen built using streamlit and deployed in the streamlit cloud. The application can be accessed using the below link.
*https://speech-recognition-system-prototype.streamlit.app/*

**Conclusion**
* High Accuracy - The model demonstrates strong performance, with accuracies above 85% on both training and test sets. This indicates that the model has learned to recognize speech patterns effectively and generalizes well to unseen data.
* Reliability -  With an accuracy of nearly 90% on the test set, the model can reliably transcribe speech into text in real-world scenarios. This reliability is crucial for applications such as voice-activated assistants, transcription services, or automated customer service systems.
* Potential for Deployment: The high accuracy suggests that the model is mature and ready for deployment in commercial settings. It could be integrated into products or services that require speech recognition capabilities, offering value to customers through improved user experience or increased efficiency.

**Future Work**
* Data Augmentation - Augment the dataset with variations in speech characteristics, such as different accents, speaking rates, and background noise conditions. This helps in improving the robustness and generalization capabilities of the speech recognition system, making it more effective in diverse real-world environments.
* Language Modeling - Integrate language modeling techniques to enhance context awareness and improve the recognition of spoken sentences. This involves training models to understand the probability of word sequences occurring together in natural language, which can help in predicting the most likely sentence given the audio input.

**References**
* Boulal, H., Hamidi, M., Abarkan, M., & Barkani, J. (2024). Amazigh CNN speech recognition system based on Mel spectrogram feature extraction method. International Journal of Speech Technology, 1-10.<br>
&nbsp;Link - *https://link.springer.com/article/10.1007/s10772-024-10100-0*
* Bankar, A., Gandhi, A., & Baviskar, D. Image and Signal Processing of Mel-Spectrograms in Isolated Speech Recognition. International Journal of Computer Applications, 183, 11-17.<br>
&nbsp;Link - *https://www.ijcaonline.org/archives/volume183/number25/bankar-2021-ijca-921625.pdf*

