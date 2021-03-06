# Advanced AI

#### Due date
:calendar: **04/04/2021**  

## :books: Subject of the project
Le contexte général de ce(s) sujet(s) est l’IA intégrant des aspects de sécurité. Sur ce domaine, plusieurs sujets sont possibles allant de :  
- la réalisation d’un état des lieux intégrant un questionnement entre les solutions développées dans la Recherche et la réalité de la mise en place d’attaques et de mécanismes de défense en conditions réelles et sur des systèmes réels.  
- L’étude d’une approche en particulier et de ses avancées comme par exemple les attaques adversaires et les mécanismes de défense associés.

> Choix: [Overview of adversarial attacks on facial recognition](https://github.com/ArianeDlns/adv-AI-project/blob/main/medium_article.md)

## :runner: Running the code

## :package: Organisation of the project

### Structure

```bash 
.
├── README.md
├── facial_recog_attack
│   ├── facial_recognition_attack.ipynb
│   ├── train_cloaked
│   │   ├── ben_afflek
│   │   ├── elton_john
│   │   ├── jerry_seinfeld
│   │   ├── madonna
│   │   ├── mindy_kaling
│   │   └── obama
│   ├── train_uncloaked
│   │   ├── ben_afflek
│   │   ├── elton_john
│   │   ├── jerry_seinfeld
│   │   ├── madonna
│   │   ├── mindy_kaling
│   │   └── obama
│   └── val
│       ├── ben_afflek
│       ├── elton_john
│       ├── jerry_seinfeld
│       ├── madonna
│       ├── mindy_kaling
│       └── obama
├── img
│   ├── Fawkes.png
│   ├── Fawkes_reference.png
│   └── features-space.png
├── medium_article.md #Medium article 
├── requirements.txt
└── scrapping_face.ipynb
```

## References 
[Amodei el al, 2016] ArXiv, abs/1606.06565. D. (2016). Concrete Problems in AI Safety. Amodei, D., Olah, C., Steinhardt, J., Christiano, P.F. Schulman, J., & Mané  

[Ren et al, 2020] Kui Ren, Tianhang Zheng, Zhan Qin, Xue Liu, Adversarial Attacks and Defenses in Deep Learning, Engineering, Volume 6, Issue 3, 2020, Pages 346-360,

https://medium.com/meetech/adversarial-learning-benchmark-evaluating-attack-and-defence-strategies-48085ab3ac3
https://github.com/cedricgoubard/benchmark-adversarial-attacks

https://towardsdatascience.com/adversarial-attacks-in-machine-learning-and-how-to-defend-against-them-a2beed95f49c

Voir aussi les travaux de Florian Tramer : https://floriantramer.com/

https://people.cs.uchicago.edu/%7Eravenben/publications/abstracts/fawkes-usenix20.html

https://github.com/ftramer/FaceCure

https://medium.com/@shikharsrivastava_14544/face-recognition-using-transfer-learning-with-vgg16-3caeca4a916e