# Overview of adversarial attacks on facial recognition
[![Theme](https://badgen.net/badge/Theme/Security&AI/blue)](https://scholar.google.fr/scholar?q=security+and+AI&hl=fr&as_sdt=0&as_vis=1&oi=scholart) 
[![Medium](https://badgen.net/badge/icon/medium?icon=medium&label)](https://medium.com/)
[![VSCode](https://badgen.net/badge/icon/visualstudio?icon=visualstudio&label)](https://github.dev/ArianeDlns/adv-AI-project/tree/main)

Authors: Valentin Bailly, Nathan Bruckmann, Ariane Dlns, Antoine Guillou-Keredan, Samuel Pujade, Lucas Sor    
Date: March 28, 2022

## Introduction : 

As artificial intelligence (AI) based tools start to get democratized amongst a wide range of users, their safety and security aspects are becoming key factors for their designs. Indeed, attacks on poorly built AI technologies might cause unintended or harmful behaviors and therefore be detrimental to users' experiences.
Today, more and more papers discuss the different types of attacks one can use to disturb an AI agent's expected behavior.In 2016, Amodei et al [1] presented a list of five practical research problems related to AI safety with ReinforcementLearning (RL) agents, categorizing them in five different categories :

- **Negative Side Effects** : The agent must not disturb its environment in a destructive manner.
- **Reward Hacking** : The reward function must not allow the agent to find “trick actions” that allow it to gain reward for undesirable actions.
- **Scalable Oversight** : The agent must respect the desired goals, even those that are scarcely visited during training.
- **Safe Exploration** : Exploration must be conducted safely
- **Robustness to Distributional Shift** : The agent must work in various environments.

In this article we will discuss Facial Recognition tools. More precisely, we will see how Reward Hacking attacks, whether they are physical or digital, can allow some users to prohibit the AIsystem behind a Facial Recognition algorithm from recognizing them and even make it recognize them as another person. In the case of digital attacks, we will showcase a specific attack paradigm called data poisoning. Finally, we will discuss how theAI system behind the Facial Recognition tool can prevent those types of attacks. 

## Facial Recognition

### Definition and stakes

The development of facial recognition system started in the 60s as a form of computer application. This kind of system aims at matching a human face from digital images against a dataset of known faces. For instance, it could be used for an identification service by measuring facial features of an individual. Today, facial recognition systems are used in by a growing number of companies and governments, from the United States with its airport biometric face scanners to China with its controversial public surveillance policy.

Now, it is clear to see that facial recognition tools call for controversial and ethical questions. First, as the technology keeps growing, getting faster and being more accurate, worries are surging about mass surveillance. Moreover, as addressed by Google in its AI responsibilities declaration, facial recognition tools must not reinforce existing biases, notably about underrepresented groups of individuals while also protecting people's privacy and being transparent.

### Technical approach

Today, models based on hand-crafted features to capture important feature information to discriminate faces have become less and less used compared to Deep Learning methods. Indeed, with larger training datasets and more precise techniques of representation, Deep Neural Networks (mostly CNNs) have become more popular. Still, hybrid approaches are rising, combining the two aforementioned methods [3].

One of the most challenging issue that comes with facial recognition tools is the occlusion challenge. When it comes to occluded faces, facial recognition tools do not perform well. While different methods are in development to take this issue into account, we can clearly see that modifying the input image by occluding parts of it or even adding accessories can result in wrong classifications. This leads us to the main topic of this article : facial recognition system attacks.

## Physical and Digital attacks

Even though they are very efficient, Face Recognition models are not invulnerable and are sometimes facing attacks. These attacks can have a different goal and can be split in two categories :

- **Targeted attacks**,  which seek to trick the FR model into recognizing a specific identity. They are also called impersonation attacks.
- **Non-targeted attacks**, whose goal is that the FR model fails to recognize the treated person, regardless of the model's output. They are also called Dodging attacks.

Most of those attacks are **adversarial attacks** [3]. They consist in modifying an original image in a way that is almost imperceptible to the human eye in order to fool a classifier into predicting the wrong class. They are particularly interesting because they are targeting Deep Neural Networks (DNNs) and Convolutional Neural Networks (CNNs) models. One of the difficulties of these attacks is that the targeted models are most of the time "black box" models, in which the architecture, the parameters or the training procedure are unknown. The attacker can however interact with the model by transferring adversarial examples.

The different attacks can be separated into 2 types:
-  **Physical attacks**, modifying the physical appearance of a face before taking the picture
- **Digital attacks**, making modifications to the captured image afterwards (mainly adversarial attacks) and which represent the majority of adversarial attacks

### Physical attacks
The majority of physical attacks are **presentation attacks** or **spoofing**. They include many techniques like wearing an accessory or imitating another person, with the aim of pretending to be another person (for example with a printed photo, a video, fake fingerprints, a 3D printed mask...). These attacks can be countered by Liveness Detection techniques that determine if the face is "alive" or real, for example by blink detection or interactive face detection.
 
Another physical attack, developed by Sharif et al. (2016) [5], is the Eyeglass Accessory Printing. It consists of wearing 3D printed paper glasses allowing a targeted attack (see example below where [...] is impersonating [...] with the glasses).
 
### Digital attacks 
A first type of digital attack is to proceed to an **image processing-based distortion**. By using deep CNN-based architecture, it is possible to modify the images to occlude some of the facial features or to add a visible noise in the image. We can mention for example grid based occlusions, eye region occlusions, forehead occlusions, most significant bit-based noise distortion…

Image processing-based distortions are however harming the quality of the input image. In some cases, the attacker may need to preserve the facial appearance of the person. Those types of attacks are called **Image De-identification**. They process an adversarial perturbation preserving the global facial quality but causing an authentication error.

**Geometric attacks** also aim to apply image modifications that are hardly visible to the human eye, by using spatial transformations of some facial elements (the shape of the face, the eyes, the nose...). Those transformations can be slight rotations, translations or scale variations for example.

<p align="center"> <img src="https://github.com/ArianeDlns/adv-AI-project/blob/main/img/digital_attack_types.png">
<p align = "center">Types of digital attacks </p>

### Defense strategies
We can find 3 categories of defense strategies against digital attacks :
- **Alteration of the input data** : a perturbation of the images, so that the model remains robust against perturbations from adversarial attacks
- **Change of the model** : an addition of an adversarial attack detection algorithm coupled with techniques to modify the architecture (e.g. dropout) in case of an attack
- **Addition of external models** to consolidate the existing model

## Fawkes & Data Poisoning

An example of such a protection tool is Fawkes, a project led by 2 PhD students at Sand Lab. It was primarily designed to help citizens protect their online privacy as some facial recognition services started downloading tons of photos of people from the internet without them being aware. 
To put a long story short, Fawkes protects your privacy by “poisoning” facial recognition models so that when they try to recognize you using a “clear” picture -i.e. a photo that hasn’t been modified by Fawkes- they won’t be able to find similarities with the “cloaked” pictures (the ones modified).
More precisely, Fawkes follows the next steps :
1. It gets a set of photos from the user that wants protection as input
2. It accesses an open set of labeled pictures and select the most dissimilar class x_T  within this set as a target
3. For each photos in the user set, it selects a picture in the target set and computes a cloak, i.e. pixel-sized modifications limited by a similarity factor φ so that the cloaked photo still looks like the original one
4. The user can now post the new photos online, and has to ensure that no clear photos are available elsewhere on the web
5. Facial recognition models will then learn from this modified photos that are mathematically different even when looking similar and won’t be able to recognize

<p align="center"> <img src="https://render.githubusercontent.com/render/math?math=max_\delta{dist(\Phi(x), \Phi(x \bigoplus \delta(x, x_T))), \text{s.t.} | \delta(x, x_T) < \phi}" width="500" alt="Fawkes distances"/> 

<p align="center"> <img src="https://github.com/ArianeDlns/adv-AI-project/blob/main/img/Fawkes_reference.png" width="700" alt="Fawkes working"/> 

This method is called “data poisoning” as it doesn’t affect the model itself but hampers its learning phase by providing altered training input. But this will only work if the model has not already been trained with clean pictures and if no or very few uncloaked photos are available online.

<p align="center"> <img src="https://github.com/ArianeDlns/adv-AI-project/blob/main/img/Fawkes.png" width="700" alt="Fawkes"/> 


## Tests and results

In order to test the Fawkes data poisoning solution, we used the facial recognition model proposed by Adam Geitgey [6]. This model consists of 4 steps: a face search based on the Histogram of Oriented Gradients method, an estimation of the positions of the facial landmarks, an encoding of the image and then a classification by SVM of this encoding.

Our test solution is as follows: from a dataset of celebrity images, we select a class that will be used as a study subject. The facial recognition model will be trained on a non-poisoned dataset, then on a dataset where the selected class will have been poisoned. Next, we will test these two facial recognition models on other non-poisoned images of the selected class, and compare the probabilities of the possible outcomes for the SVM test samples. The dataset used is an open-source dataset made of 6 classes corresponding to 6 celebrities: Ben Afflek, Elton John, Jerry Seinfield, Madonna, Mindy Kaling and Barack Obama.

The code for training the model can be found below:
 
```python
import face_recognition
from sklearn import svm
import os
import pandas as pd
import warnings
warnings.filterwarnings("ignore")

# Training the SVC classifier

# The training data would be all the face encodings from all the known images and the labels are their names
encodings = []
names = []

# Training directory
train_cloaked_dir = os.listdir('train_cloaked')
train_uncloaked_dir = os.listdir('train_uncloaked')
test_dir = os.listdir("val")

# Loop through each person in the training directory
for person in train_cloaked_dir:
    pix = os.listdir("train_cloaked/" + person)
    if person == "obama":
        pass

    # Loop through each training image for the current person
    for person_img in pix:

        # Get the face encodings for the face in each image file
        face = face_recognition.load_image_file("train_cloaked/" + person + "/" + person_img)
        face_bounding_boxes = face_recognition.face_locations(face)

        #If training image contains exactly one face
        if len(face_bounding_boxes) == 1:
            face_enc = face_recognition.face_encodings(face)[0]
            # Add face encoding for current image with corresponding label (name) to the training data
            encodings.append(face_enc)
            names.append(person)
        else:
            print(person + "/" + person_img + " was skipped and can't be used for training")

# Create and train the SVC classifier
clf_cloaked = svm.SVC(gamma='scale', probability=True)
clf_cloaked.fit(encodings,names)
```
Once these two models were trained, they were tested on the "Obama" class. Finally, the probabilities of the possible outcomes for the test samples were calculated by cross-validation. The results are as follows:

<p align="center"> <img src="https://github.com/ArianeDlns/adv-AI-project/blob/main/img/results_uncloaked.png" width="400" alt="Results of trained model on uncloaked images">
<p align = "center">Results 1 - Test results of trained model on uncloaked images </p>

<p align="center"> <img src="https://github.com/ArianeDlns/adv-AI-project/blob/main/img/results_cloaked.png" width="400" alt="Results of trained model on cloaked images">
<p align = "center">Results 2 - Test results of trained model on cloaked images </p>

As can be observed, the results decreased well in the facial recognition task on the Obama images after cloaking the images. However, cloaking does not allow the model to be fooled here. This is indeed one of the limitations of our test here, as Shan et al. indicate in their paper [2], Fawkes' data-poisoning is effective on a face recognition model like this one when it is trained on a minimum of 65 classes. This is one of the limitations of data-poisoning, discussed in the next section

## Attacks limits

Data poisoning approach suffers from some limitations, both in performances and usability. First and foremost, the data poisoning focus, as the name suggests, on the poisoning the dataset. Most studies suppose only cloaked photos are available on social media, which is highly unlikely. A balanced mix of cloaked and uncloaked images is more realistic, and is still effective as Fawkes reports 80% effectiveness is that situation. However careful examination of the dataset using a clustering approach with 2-means on each class/person would still be able to spot the cloaked and uncloaked images to eliminate the poisoned data, as their centroid in the feature space is slightly different. Anomaly detection is also able to detect cloaking if the dataset of cloaked and uncloaked image is unbalanced, or if the cloaking move the representation too far is the features space. Moreover, if face recognition system developers are aware of cloaking techniques, they are easily offset by including them in the training process. 

The second issue beside the existence of an uncloaked dataset, is the visual deformation, which remains highly visible on big pictures. In that regard, LowKey tweaks textures, an approach which is very noticeable even to unaware eyes, especially on the skin. Fawkes is more subtle and slightly displace features, or add spots. However the more subtle an approach, the less effective it is, as LowKey reports better results as Fawkes.

Finally, poisoning technics do not work well with 'toy examples' as they relies on a features space densely populated. If too few classes are used, the original image will still be the one closest to their cloaked version in the features space. The more class the better, and performances are lackluster with a number of labels in the single digit range. However this limitation is completely absent in any commercially available system, as they are designed to recognized thousands of faces.

<p align="center"> <img src="https://github.com/ArianeDlns/adv-AI-project/blob/main/img/features-space.png" width="400" alt="Features space"/> 

## References 

[1] [Amodei et al, 2016] Amodei, D., Olah, C., Steinhardt, J., Christiano, P.F., Schulman, J., & Mané, D. (2016). Concrete Problems in AI Safety. ArXiv, abs/1606.06565.

[2] [Shan et al, 2020] Shawn Shan, Emily Wenger, Jiayun Zhang, Huiying Li, Haitao Zheng, and Ben Y. Zhao. Fawkes: Protecting Personal Privacy against Unauthorized Deep Learning Models.In Proceedings of USENIX Security Symposium 2020. 

[3] [Biswas et al, 2021] Rubel Biswas, Pablo Blanco-Medina (Aug. 2021). State of the Art : Face Recognition. ArXiv abs/2108.11821.

[4] [Tramer et al, 2021] Evani Radiya-Dixi, Florian Tramèr (2021). Data Poisoning Won’t Save You From Facial Recognition. ArXiv:2106.14851.

[5] [Sharif et al, 2016] Sharif, Mahmood & Bhagavatula, Sruti & Bauer, Lujo & Reiter, Michael. (2016). Accessorize to a Crime: Real and Stealthy Attacks on State-of-the-Art Face Recognition. 1528-1540. 10.1145/2976749.2978392. 

[6] [Adam Geitgey, 2016] Adam Geitgey (2016). Face Recognition. https://face-recognition.readthedocs.io/en/latest/readme.html
