# Sécurité et IA

# Overview of adversarial attacks on facial recognition

## Introduction : 

As artificial intelligence (AI) based tools start to getdemocratized amongst a wide range of users, their safety andsecurity aspects are becoming key factors for their designs.Indeed, attacks on poorly built AI technologies might  causeunintended or harmful behaviors and therefore be detrimental tousers' experiences.
Today, more and more papers discuss the different types ofattacks one can use to disturb an AI agent's expected behavior.In 2016, Amodei et al [1] presented a list of five practicalresearch problems related to AI safety with ReinforcementLearning (RL) agents, categorizing them in five differentcategories :

- **Negative Side Effects** : The agent must not disturb its environment in a destructive manner.
- **Reward Hacking** : The reward function must not allow the agent to find “trick actions” that allow it to gain reward for undesirable actions.
- **Scalable Oversight** : The agent must respect the desired goals, even those that are scarcely visited during training.
- **Safe Exploration** : Exploration must be conducted safely
- **Robustness to Distributional Shift** : The agent must work in various environments.

In this article we will discuss Facial Recognition tools. Moreprecisely, we will see how Reward Hacking attacks, whether theyare physical or digital, can allow some users to prohibit the AIsystem behind a Facial Recognition algorithm from recognizingthem and even make it recognize them as another person. In thecase of digital attacks, we will showcase a specific attackparadigm called data poisoning. Finally, we will discuss how theAI system behind the Facial Recognition tool can prevent thosetypes of attacks. 

## Facial Recognition

### Definition and stakes

The development of facial recognition system started in the 60s as a form of computer application. This kind of system aims at matching a human face from digital images against a dataset of known faces. For instance, it could be used for an identification service by measuring facial features of an individual. Today, facial recognition systems are used in by a growing number of companies and governments, from the United States with its airport biometric face scanners to China with its controversial public surveillance policy.

Now, it is clear to see that facial recognition tools call for controversial and ethical questions. First, as the technology keeps growing, getting faster and being more accurate, worries are surging about mass surveillance. Moreover, as adressed by Google in its AI responsibilities declaration, facial recognition tools must not reinforce existing biases, notably about underrepresented groups of individuals while also protecting people's privacy and being transparent.

### Technical approach

Today, models based on hand-crafted features to capture important feature information to discriminate faces have become less and less used compared to Deep Learning methods. Indeed, with larger training datasets and more precise techniques of representation, Deep Neural Networks (mostly CNNs) have become more popular. Still, hybrid approaches are rising, combining the two aforementionned methods [3].

One of the most challenging issue that comes with facial recognition tools is the occlusion challenge. When it comes to occluded faces, facial recognition tools do not perform well. While differents methods are in development to take this issue into account, we can clearly see that modifiying the input image by occluding parts of it or even adding accessories can result in wrong classifications. This leads us to the main topic of this article : facial recognition system attacks.

## Physical and Digital attacks



## Fawkes & Data Poisoning

An example of such a protection tool is Fawkes, a project led by 2 PhD students at Sand Lab. It was primarily designed to help citizens protect their online privacy as some facial recognition services started downloading tons of photos of people from the internet without them being aware. 
To put a long story short, Fawkes protects your privacy by “poisoning” facial recognition models so that when they try to recognize you using a “clear” picture -i.e. a photo that hasn’t been modified by Fawkes- they won’t be able to find similarities with the “cloaked” pictures (the ones modified).
More precisely, Fawkes follows the next steps :
1. It gets a set of photos from the user that wants protection as input
2. It accesses an open set of labeled pictures and select the most dissimilar class within this set as a target
3. For each photos in the user set, it selects a picture in the target set and computes a cloak, i.e. pixel-sized modifications limited by a similarity factor so that the cloaked photo still looks like the original one
4. The user can now post the new photos online, and has to ensure that no clear photos are available elsewhere on the web
5. Facial recognition models will then learn from this modified photos that are mathematically different even when looking similar and won’t be able to recognize

<p align="center"> <img src="https://github.com/ArianeDlns/adv-AI-project/blob/main/img/Fawkes.png" width="400" alt="Fawkes"/> 

## Tests and results



## Attacks limits




## References 

[1] : [Amodei el al, 2016] Amodei, D., Olah, C., Steinhardt, J., Christiano, P.F., Schulman, J., & Mané, D. (2016). Concrete Problems in AI Safety. ArXiv, abs/1606.06565.

[2] Fawkes: Protecting Personal Privacy against Unauthorized Deep Learning Models.
Shawn Shan, Emily Wenger, Jiayun Zhang, Huiying Li, Haitao Zheng, and Ben Y. Zhao.
In Proceedings of USENIX Security Symposium 2020. 

[3] : Rubel Biswas, Pablo Blanco-Medina (Aug. 2021). State of the Art : Face Recognition. ArXiv abs/2108.11821.

