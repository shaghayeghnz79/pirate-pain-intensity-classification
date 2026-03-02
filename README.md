# pirate-pain-intensity-classification

This project presents a deep learning approach for classifying pain intensity from 3D skeletal motion data, created as part of the Pirate Pain Intensity Classification Challenge. Each sample in the dataset contains 31 skeletal joint measurements recorded across 160 timesteps, and the task is to predict whether the subject is experiencing no pain, low pain, or high pain. The data presents several challenges, including severe class imbalance—where the high-pain category appears rarely—and noisy or low-variance joint channels that require careful preprocessing.

To address these issues, we developed two temporal deep learning architectures designed to capture both short-range and long-range motion dynamics. The first model combines Bidirectional LSTMs with Multi-Head Self-Attention, allowing the network to learn temporal dependencies and focus on the most informative moments within each sequence. Oversampling and hyperparameter tuning were used to handle class imbalance and stabilize performance, resulting in a strong macro-F1 score of around 0.94.

The second model integrates 1D-CNN layers, stacked BiLSTMs, and a custom attention mechanism. This architecture is designed to pick up detailed local motion patterns through convolutional filters while still modeling long-term temporal structure using recurrent layers. A dedicated branch processes the available survey metadata, which is fused with motion features before the final prediction. Test-Time Augmentation (TTA) further improves generalization. This model performed slightly better, reaching a macro-F1 of around 0.95 across five cross-validation folds.

Both models were trained using oversampling and monitored through macro-F1 rather than accuracy, since accuracy is misleading under class imbalance. Additional feature engineering—such as computing statistical descriptors for joints and metadata—helped capture subtle variations in the motion sequences. Overall, both architectures generalize well, with the second showing stronger robustness thanks to the combination of CNNs, LSTMs, metadata integration, and a custom attention mechanism.

Future improvements could explore transformer-based sequence models, more extensive augmentation strategies, and denoising techniques for joint trajectories. This project demonstrates the effectiveness of combining temporal modeling, attention mechanisms, and metadata fusion for human-motion-based pain classification.

## Team / Contributors
- [Amirali Askari](https://www.linkedin.com/in/amirali-askari-874263264/) (GitHub: [@amiraliaskari2014](https://github.com/amiraliaskari2014)) (GitHub: @amiraliaskari2014 ) 
## Report and Required Data
Report: [Project Report (PDF)](https://drive.google.com/file/d/1UsHJz0IRaBnknXr7svaC6fxXO9HfVLs7/view?usp=sharing)
Download: [Dataset (Google Drive)](https://drive.google.com/file/d/1cbYSYR5HkYrwpVRZ-OkbD0Jpq_wsLahk/view?usp=sharing)
