# Multimedia Knowledge Graph

Jipeng Zhang

---

> - Multimedia Knowledge Graph Construction
>   - multimodal relation extraction
>   - multimodal entity recognition and linking
>   - multimodal embedding 
> - Multimedia Knowledge Graph Representation Learning
> - Scene Graph 

---

## 1. multimedia knowledge graph construction

__

[**Image-embodied Knowledge Representation Learning**](https://arxiv.org/pdf/1609.07028.pdf) [[project page](<https://github.com/thunlp/IKRL>)] 

Ruobing Xie, Zhiyuan Liu, Huanbo Luan, Maosong Sun (IJCAI'17)

Introduces the new task: image based multimedia knowledge graph. Given the corresponding images of entities, we need to generate the representation of these images in KG. (We notice that this task did not consider constructing new and specific relations for these images.) This paper creates a new dataset WN9-IMG and develops a multimedia graph embedding methods based on TransE. 

- data source: WN9-IMG (A subset of WN18 constructed by their own. Each entity contains a certain number of images.)
- modeling technique: $E_{SS} = ||h_S+r-t_S||$, $E_{II} = ||h_I+r-t_I||$, $E_{SI} = ||h_S+r-t_I||$, $E_{IS} = ||h_I+r-t_S||$. The core component is the attention based image encoder that combine all the image features of the specific entity into a single image feature.
- evaluation downstream task: 
  - **Knowledge Graph Completion** (complete a triple $(h,r,t)$ when one of $h, r, t$ is missing), 
  - **Triple Classification** (predict whether a triple fact $(h,r,t)$ is correct or not according to the dissimilarity function)
  - Case Study task, **Semantic Regularities of Images**, **Capability of Attention**

[Adaptive Co-Attention Networkfor Named Entity Recognition in Tweets](https://pdfs.semanticscholar.org/5ca1/c595708d22d92b3f913be391575560bdab2c.pdf?_ga=2.258610882.953046097.1557891086-1745154373.1553132250) *AAAI 18*

[MMKG: Multi-Modal Knowledge Graphs](https://arxiv.org/pdf/1903.05485.pdf)  *Arxiv 19*

[Zero shot Multimodal Named Entity Disambiguation for Noisy Social Media Posts](https://vitordecarvalho.github.io/papers/acl2018_NED.pdf) *ACL 2018*

[Multimodal Named Entity Recognition for Short Social Media Posts](https://www.aclweb.org/anthology/N18-1078) *NAACL 2018*

2. multimedia knowledge graph representation learning

[Image-embodied Knowledge Representation Learning](https://arxiv.org/pdf/1609.07028.pdf) *IJCAI 17*

[**A Multimodal Translation-Based Approach for Knowledge Graph Representation Learning**](https://pdfs.semanticscholar.org/be91/946bedbf65d543a7eb9dd1e033e7aaf78c3c.pdf?_ga=2.239204043.953046097.1557891086-1745154373.1553132250) [[project page](<https://github.com/UKPLab/starsem18-multimodalKB>)] *SEM@NAACL 2018*

(They also found that TransE fails to create suitable representation for entities that appear frequently as the head/tail of one-to-many/many-to-one relations.) This paper's motivation is to explore KG representation learning that leverages linguistic and visual information. Propose to fuse visual and linguistic features to represent entities, present a new large-scale dataset for multimodal KGC based on Freebase and consider other kinds of lingu+-istic information. 

- data source: WN9-IMG, FB-IMG (Require entities from FB15k, a subset of Freebase, and collect 10 images for each entity. This dataset is much larger than WN9-IMG.)
- modeling technique: 
  - new entity representation learning method: $h_m = h_w\oplus h_i$, $t_m = t_w\oplus t_i$, $\oplus$ can be concatenation, DeViSE and Imagined method
  - new energy function: $E_{M1}=||h_m+r_s-t_m||​$, $E_{M2}=||(h_m+h_s)+r_s-(t_m+t_s)||​$, $E_{SM}=||h_s+r_s-t_m||​$, $E_{Ms}=||h_m+r_s-t_s||​$,
- evaluation downstream task
  - **Link Prediction**, **Triple Classification**

[**Embedding Multimodal Relational Data for Knowledge Base Completion**](<https://arxiv.org/abs/1809.01341>) [[project page](<https://github.com/pouyapez/mkbe>)]*EMNLP 18*

Introduce additional neural encoders to embed multimodal evidence types and neural decoders that use an entity's embedding to generate its multimodal attributes (like image and text). They showed three motivations: entity features should apply multimodal information; multimodal value should be able to be predicted; enumeration is no possible for unseen nodes. 

- data source: MovieLens-100k (except existing relations, Rating is also used as the relation between users and movies, they are augmented with movie posters collected from TMDB), YAGO-10 (extend this dataset with textual description and images from DBpedia)
- modeling technique: 
  - encoding: structure knowledge (embed their one-hot encoding), numerical (project them with a specific fully-connected layer), text (*short*: embedding with GRU; *long*: embedding with CNN), image (VGG with compact bilinear pooling)
  - decoding: numerical and categorical data (a feed-forward network for generating corresponding data), text (adversarially regularized autoencoder, i,e,. ARAE), image (pix2pix GAN)
- evaluation downstream task: link prediction

3. scene graph

Here, I found a great collection of scene graph related paper http://picdataset.com/challenge/paper_list/.

[Representation Learning for Scene Graph Completion viaJointly Structural and Visual Embedding](https://www.ijcai.org/proceedings/2018/0132.pdf) *IJCAI 18*

[Visual Relationship Detection with Language Priors](https://arxiv.org/abs/1608.00187) *ECCV 16*

[Scene Graph Generation by Iterative Message Passing](https://arxiv.org/abs/1701.02426) *CVPR 17*

[Scene Graph Generation from Objects, Phrases and Region Captions](https://arxiv.org/abs/1707.09700) *ICCV 17*

[Detecting Visual Relationship with Deep Relational Networks](https://arxiv.org/abs/1704.03114) *CVPR 17*

[Visual Translation Embedding Network for Visual Relation Detection](https://arxiv.org/abs/1702.08319) *CVPR 17*

[ViP-CNN: Visual Phrase Guided Convolutional Neural Network](https://arxiv.org/abs/1702.07191) *CVPR 17*

[Deep Variation-structured Reinforcement Learning for Visual Relationship and Attribute Detection](https://arxiv.org/abs/1703.03054) *CVPR 17*

[Neural Motifs: Scene Graph Parsing with Global Context](https://arxiv.org/abs/1711.06640) *CVPR 18*

[Pixels to Graphs by Associative Embedding](https://arxiv.org/abs/1706.07365) *NIPS 17*

[Graph R-CNN for Scene Graph Generation](https://arxiv.org/abs/1808.00191)  *ECCV 18*

[Factorizable Net: An Efficient Subgraph-based Framework for Scene Graph Generation](https://arxiv.org/abs/1806.11538) *ECCV 18*

[Mapping Images to Scene Graphs with Permutation-Invariant Structured Prediction](https://arxiv.org/abs/1802.05451) *NIPS 18*

[LinkNet: Relational Embedding for Scene Graph](https://papers.nips.cc/paper/7337-linknet-relational-embedding-for-scene-graph) *NIPS 18*



