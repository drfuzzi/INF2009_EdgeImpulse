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


10. **Train Model**:
   - Once you have collected enough labeled data, train your machine learning model using Edge Impulse:
     ```
     edge-impulse-daemon
     ```
   - Follow the instructions to train your model using the collected data.

11. **Deploy Model to Raspberry Pi 4**:
   - Deploy your trained model to your Raspberry Pi 4:
     ```
     edge-impulse-run-impulse
     ```
   - Follow the prompts to download and deploy the model to your Raspberry Pi 4.

11. **Interact with Model**:
   - Use the deployed model on your Raspberry Pi 4 to perform inference on new sensor data.
   - Follow the instructions provided by Edge Impulse to interact with your deployed model.

### Additional Resources:
- [Edge Impulse Documentation](https://docs.edgeimpulse.com/)
- [Edge Impulse Community Forum](https://forum.edgeimpulse.com/)
- [Raspberry Pi Documentation](https://www.raspberrypi.org/documentation/)

By following these steps, you'll be able to create an Edge Impulse account, set up, and use Edge Impulse on your Raspberry Pi 4 for collecting sensor data, training machine learning models, and deploying them for inference on-device.
