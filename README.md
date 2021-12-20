# WGAN-for-toupathy
## An application of deep generative model for dissecting molecular features in the early stage of tauopathy  

### [Prerequisites]
* __Create virtual environment__  

          virtualenv WGAN_toupathy -p python3
          
          source WGAN_toupathy/bin/activate  

* __Install packages__  
    
               pip install -r requirements.txt

### [Usage]
__Train and Analysis using WGAN_for_toupathy.ipynb__

  * __Schematic overview of GAN training__    
![GAN_overveiw](https://user-images.githubusercontent.com/57948381/146506692-1ca33fc7-4497-4ab5-bc37-d189874f54a2.png)
    * We adopted the advanced Wasserstein GAN with gradient penalty, which consists of two networks, generator and discriminator, and contains several advanced features for learning. We set the number of hidden layer units for the generator and discriminator to 450 and 270, respectively. Thus, the architecture of the generator and discriminator were input FC (100)—leaky ReLU—hidden FC (450)—leaky ReLU—hidden FC (450)—leaky ReLU—output FC (3,767); and input FC (3,767)—leaky ReLU—hidden FC (270)—leaky ReLU—hidden FC (270)—leaky ReLU—output FC (1), respectively. The weights were updated by learning based on the loss of the Wasserstein GAN with gradient penalty (gradient penalty = 10) with Adam optimiser (learning rate = 1e-5) for 300,000 epochs with a minibatch size of 32.<br/>  
  * __GAN model training and evaluation__
  
    ![github_upload_1](https://user-images.githubusercontent.com/57948381/146507328-5bd128ec-cd44-4556-9ab0-56fa533482e8.png)
    * The left image shows the Generator and Discriminator network loss curves. The image on the right is a t-SNE projection of 380 training samples, 84 generated samples, and 20 real samples at 0, 100K, 200K, and 300K training steps.<br/>  
    
    ![github_upload_2](https://user-images.githubusercontent.com/57948381/146507878-45aaa9fc-1696-47db-8bd1-076aa8fc4247.png)
    * Distribution of rescaled RLD for real and generated samples after 300K training steps. Distribution of correlation coefficients between pairs of real or generated samples after 300K training steps.<br/>   
    ![github_upload_3](https://user-images.githubusercontent.com/57948381/146508262-2144849e-e21b-4b23-ad90-a517e5dce421.png)<br/>  <br/>  
    * t-SNE projection of 20 real samples (upper left), 360 generated samples (upper right), and 20 resembled generated samples (bottom). Correlation coefficient between real and resembled generated samples during training steps.<br/>  

* __Pattern clustering and grouping of 3,767 TCs__<br/>  
![tc_allpattern_P1](https://user-images.githubusercontent.com/57948381/146508980-8a605d63-da3b-491a-b64f-447c7561e72c.jpeg)<br/>  
  * The extracted 3,381 TCs were merged into 50 clusters, which were grouped into eight patterns by direction (upward or downward).
