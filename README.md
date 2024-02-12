### Guide on how to use Edge Impulse with the Raspberry Pi 400 + Webcam

#### Materials Needed
- Raspberry Pi 400
- MicroSD card with Raspberry Pi OS
- Logitech C310 HD Webcam
- Internet connection (Mobile Hotspot)

### Steps:

1. **Create Edge Impulse Account**:
   - Visit the [Edge Impulse website](https://studio.edgeimpulse.com/login) in your web browser.
   - Click on "Sign Up" located below the Log in button.
   - Fill out the registration form with your details.
   - Finally Click on the "Sign Up" button to create your Edge Impulse account.

2. **Installing Edge Impulse on your Raspberry Pi 400**:
   - Follow the guide [here](https://docs.edgeimpulse.com/docs/development-platforms/officially-supported-cpu-gpu-targets/raspberry-pi-4).
   - You must use 64-bit OS with _aarch64; 64-bit version.
   - Installing dependencies by running the following commands:
    ```
    sudo apt update
    curl -sL https://deb.nodesource.com/setup_18.x | sudo bash -
    sudo apt install -y gcc g++ make build-essential nodejs sox gstreamer1.0-tools gstreamer1.0-plugins-good gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps
    sudo npm install edge-impulse-linux -g --unsafe-perm
    ```
     
3. **Connecting to Edge Impulse**:
   - With all dependencies setup, connect your webcam to your Raspberry Pi 400 (`sudo` is to ensure your devices can be accessed), and run:
   ```
   sudo edge-impulse-linux
   ```
   - Note that at this point, the images from the webcam can be captured but **does not work** during model training. Therefore, I would only suggest audio based tutorials.
   - To join another project, use the following command: `sudo edge-impulse-linux --clean`.
   - Enter the credential you use to sign up for Edge Impulse website.
   - Select the project you would like to load (you will need to do step #4 before you may proceed)
   - Select your webcam: `USB-Audio - USB Device 0x`.
  
4. **Clone Project**:
   - You may create a clone of the following project [Tutorial: Recognize sounds from audio](https://studio.edgeimpulse.com/studio/348213).
   - You may follow the guide [here](https://docs.edgeimpulse.com/docs/tutorials/end-to-end-tutorials/audio-classification) for the above tutorial.
   - Click on the "Clone this project" button located on the top right of the page.
   - Click on the green "Clone project" button.
   - You can confirm this works (the project will be listed) by logging into Edge Impulse with the created account.

   ![image](https://github.com/drfuzzi/INF2009_EdgeImpulse/assets/108112390/ce054cee-507c-4086-8f68-974af72cce9b)

5. **Data Acquisition: Acquire Sensor Data**:
   - Collect sensor data for your project. This can be done using a compatible sensor connected to your Raspberry Pi 400.
   - Follow the instructions provided by Edge Impulse to collect and label your sensor data.
   - Ensure that Step #3 is successful and you will see a green dot as follows.
  
   ![image](https://github.com/drfuzzi/INF2009_EdgeImpulse/assets/108112390/669ba1b6-95bd-46e2-b1a7-0de8aa0a5f74)

   - Select `Microphone` and the appropriate sample length before clicking on `Start sampling` button.
   ![image](https://github.com/drfuzzi/INF2009_EdgeImpulse/assets/108112390/4c0b94cb-1bc5-44f5-8bdc-3315d5ef6a84)

   - A new data will be included into the dataset. This dataset can be split into smaller samples if necessary.
   - The tutorial have included 2 types of data; noise and faucet. You may include a third one. However, you will have you incorporate significantly more data for the model to be able to identify the new category well.
   - You will also be required to split the training and testing dataset as shown below:

   ![image](https://github.com/drfuzzi/INF2009_EdgeImpulse/assets/108112390/e9a80513-df54-4c21-94eb-f6c5b6302cdb)

6. **Training the Model**:

   - Select `Create impulse` under `Impulse design`. Leave the rest as default (for now) and click on the green `Save Impulse` button.
  
   ![image](https://github.com/drfuzzi/INF2009_EdgeImpulse/assets/108112390/8506572e-e37c-43cf-bb42-3b1ba01feaeb)

   - Select `Spectogram` under `Impulse design`. Select on `Generate features` (besides `Parameters`) and click on the blue `Generate features` button.  Wait till the `Job completed (success)` notification appears.

   ![image](https://github.com/drfuzzi/INF2009_EdgeImpulse/assets/108112390/92316101-5cdf-49ec-bd85-ced8c0cca2ef)

   - Select `NN Classifier` under `Impulse design`. Click on the green `Start training` button.  Ensure the target is Raspberry Pi 4 before pressing the green button.
   ![image](https://github.com/drfuzzi/INF2009_EdgeImpulse/assets/108112390/9243b481-f48f-4050-9eee-cdb5ab6971cb)
   - Wait till the `Job completed (success)` notification to appear.


7. **Deploy Model to Raspberry Pi 400**:
   - Press Ctrl-C to stop the script on the Raspberry Pi 400.
   - Deploy your trained model to your Raspberry Pi 400 by executing the following command:
     ```
     sudo edge-impulse-linux-runner
     ```
   - Follow the prompts to download and deploy the model to your Raspberry Pi 400.

8. **Interact with Model**:
   - The model will be deployed immediately and the microphone will feed all the sounds to the model.
   - Follow the is a sample of the output:
   ```
   classifyRes 1ms. { faucet: '0.2963', noise: '0.7037' }
   classifyRes 1ms. { faucet: '0.0533', noise: '0.9467' }
   classifyRes 1ms. { faucet: '0.0371', noise: '0.9629' }
   classifyRes 1ms. { faucet: '0.0231', noise: '0.9769' }
   classifyRes 1ms. { faucet: '0.0231', noise: '0.9769' }
   classifyRes 1ms. { faucet: '0.0136', noise: '0.9864' }
   ```
   - The model is classifying input data into two categories: "faucet" and "noise". The numbers associated with each category represent the model's confidence score or probability estimation for each class. In the first example, the model predicts with a probability of approximately 29.63% that the input belongs to the "faucet" class and approximately 70.37% that it belongs to the "noise" class. In addition, the classification result was obtained in 1 millisecond.
