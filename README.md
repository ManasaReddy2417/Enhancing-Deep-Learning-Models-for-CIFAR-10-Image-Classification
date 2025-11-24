# Enhancing-Deep-Learning-Models-for-CIFAR-10-Image-Classification
Enhancing Deep Learning Models for CIFAR-10 image recognition — progression from FCN → CNN → augmented CNN with modern schedulers and optimizers, reaching ~90% accuracy on several classes.

This repository contains the code, experiments, and notes for “Enhancing Deep Learning Models for Image Recognition in CIFAR-10.” The aim was to evaluate how model architecture choices and modern training practices affect classification accuracy and generalization on CIFAR-10 (60,000 32×32 color images across 10 classes). We compare a baseline fully connected network (FCN), a vanilla CNN, CNNs with max-pooling, and CNNs with systematic data augmentation and regularization; finally we apply advanced optimizers and LR schedulers to maximize performance. Results, per-class performance, training curves, and single/batch prediction examples are included.

Step-by-step process:
1. Problem definition & dataset - Choose CIFAR-10 as the benchmark dataset (50k train / 10k test, 10 classes, 32×32 RGB).
2. Set up environment & tooling - Use Python and PyTorch for model implementation and training.
3. Baseline model — Fully Connected Network (FCN) - Implement an FCN with three hidden layers (512 units each) and ReLU activations. Train with CrossEntropyLoss and SGD for baseline performance measurement.
4. Vanilla CNN - Implement a simple CNN with three convolutional layers (kernel size 3, 16 filters as starting point), ReLU, and SGD training for comparison.
5. Add pooling and deeper blocks - Introduce MaxPooling to reduce spatial dims and increase computational efficiency; expand filter counts per block.
6. Introduce data augmentation and regularization - Apply transforms such as RandomHorizontalFlip and RandomCrop. Build convolutional blocks: Conv → BatchNorm → ReLU → Conv → BatchNorm → ReLU → MaxPool → Dropout(0.25).Double filters across blocks to increase representational capacity.
7. Advanced training techniques - Experiment with learning-rate schedulers: StepLR and Cosine Annealing. Try modern optimizers like AdamW (and AdamW + Cosine annealing).
8. Training, evaluation & diagnostics - Track train/test loss and accuracy over epochs; produce accuracy vs epoch plots and per-class confusion/accuracy breakdowns. Evaluate single image and batch predictions to validate qualitative behavior.
9. Analysis & iteration - Compare architecture+training variants, identify classes with weaker performance (Cats, Dogs, Birds) and classes with strong performance (Cars, Ships, Trucks, Plane, Frog, Horse, Deer).

What we achieved (concise bullets)

1. Baseline FCN and vanilla CNN performed poorly (<50% accuracy). 
2. Adding pooling, augmentation and regularization improved results (around ~70% accuracy). 
3. Using modern optimizers and LR schedulers (AdamW, Cosine Annealing, StepLR) further boosted performance — overall best models reached roughly 90% accuracy on several classes and strong overall accuracy. 
4. Observed class-wise variation: classes with distinct visual features (car, ship, truck, plane, horse, frog, deer) achieved >90%; visually similar/ambiguous classes (cat, dog, bird) remained harder (70–89%).

Conclusion:
Systematic model improvements — moving from a simple FCN to deeper CNNs, applying data augmentation, batch normalization, dropout, and then tuning optimizers and LR schedulers — significantly improved CIFAR-10 classification performance. The project demonstrates that architecture plus training methodology both matter: augmentation and modern optimization were the most impactful for raising accuracy and generalization across classes.
