Abstract :
1. Aligning multiple modalities give good results (text to image or image captioning).
2. CLIP fails on acuteness or uncommon ones.
3. Also human poses can be generated from both text and image.

-- By above 3 points This paper is came with combining 3D poses, person's pictures and textual pose descriptions to produce an enhanced 3D-, visual- and semantic-aware human pose representation.

-- Also we test this pose embroider project on 2 tasks
a) SMPL regression from image with optional text cue
b) fine-grained instruction generation, which consists
in generating a text that describes how to move from one 3D pose to
another (as a fitness coach)

---------------------------

Introduction :
 In summary, our contributions list as follow:
✽ We introduce a new framework to embroider together several human pose related modalities and derive a rich semantic-, visual-, 3D-aware pose embedding space (Section 3), We train it on the adapted BEDLAM-Script dataset
(a description-augmented version of BEDLAM [6]). As a direct side-product,
we present results for any-to-any multi-modal retrieval (Section 4).
✽ We showcase an application of the proposed enhanced pose representation
for the task of pose instruction generation (Section 5). Although our method
is almost exclusively trained on synthetic data (the proposed BEDLAM-Fix
dataset), we obtain promising results on real-world images.
✽ We illustrate SMPL regression as another application (Section 6).

---------------------------------

Related works:
1) Pose script and Chat pose -- works existing on text -> pose
2) Image bind , Omnivore
3) NeXT-GPT -- any to any generation Existing model
4) Fix My-Pose -- For pose instruction generation

----------------------------------

Pose Embroider framework :
See Fig2 in research paper
Encoders -> {v,p,t} ->linear layer followed by relu -> transformer -> xG_bar -> MLP -> {v^,p^,t^} -> compare with {v,p,t} contrastive loss.

encoders : 
  a) vision - VisionTransformer tuned on human data to encode images
  b) pose   - a variant of VPoser trained on 22 body joints
  c) text   - DistilBERT
all encoders are frozen.

Middle layer + transformer work

Training :
1) to train xG_bar, we project it back to each modality space thanks to
expendable modality-specific multi-layer perceptrons(MLPs). These yield
mˆ G ∈ MˆG := {vˆG, pˆG,tˆG}
2) Then for a batch we compute contrastive loss
3) then Update the learnable parameters

---------------------------------

DataSet : BELDAM-Script
This datset consists of (HumanImage,Its 3d pose, Text description of pose)
we train our pose Embroider on it.


-----------------------------------

Github link - https://github.com/naver/poseembroider

