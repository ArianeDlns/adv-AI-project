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

The development of facial recognition system started in the 60s as a form of computer application. This kind of system aims at matching a human face from digital images against a dataset of known faces. For instance, it could be used for an identification service by measuring facial features of an individual. Today, facial recognition systems are used in by a growing number of companies and governments, from the United States with its airport biometric face scanners to China with its controversial public surveillance policy.

Now, it is clear to see that facial recognition tools call for controversial and ethical questions. First, as the technology keeps growing, getting faster and being more accurate, worries are surging about mass surveillance. Moreover, as adressed by Google in its AI responsibilities declaration, facial recognition tools must not reinforce existing biases, notably about underrepresented groups of individuals while also protecting people's privacy and being transparent.

## Physical and Digital attacks



## Fawkes & Data Poisoning



## Tests and results



## Attacks limits




## References 

[1] : [Amodei el al, 2016] Amodei, D., Olah, C., Steinhardt, J., Christiano, P.F., Schulman, J., & Mané, D. (2016). Concrete Problems in AI Safety. ArXiv, abs/1606.06565.

[2] Fawkes: Protecting Personal Privacy against Unauthorized Deep Learning Models.
Shawn Shan, Emily Wenger, Jiayun Zhang, Huiying Li, Haitao Zheng, and Ben Y. Zhao.
In Proceedings of USENIX Security Symposium 2020. 

[3] 

