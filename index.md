1. Modular Artefact Inventory (Units 1–12)
The e-portfolio is published via GitHub Pages, systematically capturing artefacts, collaborative wiki contributions, code repositories, team meeting logs, and tutor/peer feedback across all twelve units of the module.

Unit 1: Machine Learning Landscape & Taxonomy
Artefact: Collaborative Discussion Contribution on supervised versus unsupervised paradigms in enterprise automation.
LSEP Focus: Professional accountability, determining operational failure modes and boundary risks in automated pipelines.
Feedback Loop: Peer feedback noted an over-reliance on heuristic rules; integrated formal mathematical loss formulations in follow-up postings.
Unit 2: Mathematical Foundations & Exploratory Data Analysis (EDA)
Artefact: Jupyter Notebook analyzing statistical distributions, skewness correction, and covariance matrices across high-dimensional feature spaces.
LSEP Focus: Understanding dataset limitations, data provenance, selection bias, and data hygiene.
Feedback Loop: Tutor highlighted collinearity risks in medical imaging features; integrated Box-Cox power transformations and variance inflation factor (VIF) checks.
Unit 3: Classical Supervised Learning: Linear Models & SVMs
Artefact: Script and benchmark comparing linear classification against Support Vector Machines (SVM) using Radial Basis Function (RBF) kernels on non-linearly separable data.
LSEP Focus: Algorithmic transparency; comparing deterministic mathematical decision boundaries against unconstrained heuristic spaces.
Feedback Loop: Peer review identified high test inference latency with RBF kernels; benchmarked linear dual-space approximations.
Unit 4: Ensemble Methods & Decision Trees
Artefact: Collaborative Wiki contribution on variance-bias trade-offs in Gradient Boosting (XGBoost) versus Random Forests.
LSEP Focus: Algorithmic fairness; how bagging versus boosting impacts outlier sensitivity and vulnerable demographic fringe cases.
Feedback Loop: Resolved team debates regarding early stopping criteria and hyperparameter tuning protocols.
Unit 5: Unsupervised Learning & Dimensionality Reduction
Artefact: Comparative analysis notebook evaluating PCA, t-SNE, and UMAP projections on latent feature representations.
LSEP Focus: Data privacy; auditing risks associated with latent attribute reconstruction from low-dimensional embeddings.
Feedback Loop: Tutor advised caution regarding information loss in PCA eigenvalues; incorporated scree plot cumulative variance thresholds (95%).
Unit 6: Project Proposal & System Design (Milestone 1)
Artefact: Summative Team Proposal Document: system requirements, architectural blueprint, and risk mitigation register for automated medical triage.
LSEP Focus: Legal compliance (GDPR/HIPAA), institutional patient consent, and stakeholder risk governance.
Feedback Loop: Tutor feedback commended ambitious clinical framing but mandated strict validation set isolation and explicit mitigation of severe class imbalance.
Unit 7: Neural Networks & Deep Representation Learning
Artefact: PyTorch pipeline implementing a multi-layer perceptron from scratch with custom backpropagation, dropout, and AdamW optimization.
LSEP Focus: Intellectual property of model parameters; ethical trade-offs between manual domain features and automated end-to-end representations.
Feedback Loop: Team code review standardized gradient clipping thresholds and modular forward/backward tensor passes.
Unit 8: Convolutional Architectures & Computer Vision
Artefact: Comparative notebook analyzing CNN spatial invariance, receptive fields, and feature map activations across radiographic images.
LSEP Focus: Social impact; diagnostic disparities arising from heterogeneous scanning hardware and resolution variations across clinics.
Feedback Loop: Addressed vanishing gradient issues by adopting residual skip-connection architectures (ResNet blocks).
Unit 9: Model Evaluation, Validation & Data Leakage
Artefact: Comprehensive validation protocol using Stratified 5-Fold Cross-Validation isolating patient-level spatial splits.
LSEP Focus: Scientific integrity; preventing cross-patient data leakage between training, validation, and holdout testing partitions.
Feedback Loop: Tutor feedback praised stratified partitioning; advised tracking patient ID metadata across hospital recording sources.
Unit 10: Explainable AI (XAI) & Algorithmic Auditing
Artefact: Diagnostic implementation of Gradient-Weighted Class Activation Mapping (Grad-CAM) and SHAP feature attributions on radiographic models.
LSEP Focus: Ethical explainability; the moral and clinical necessity of auditable reasoning in automated diagnostic decision-making.
Feedback Loop: Team identified false positive activations caused by peripheral radiograph annotations; added border-cropping preprocessing.
Unit 11: Comparative Study & System Implementation (Milestone 2)
Artefact: Summative individual recorded presentation (20 min), slide deck, transcript, and reproducible Jupyter notebook comparing Classical SVM vs ResNet-18 for pneumonia detection.
LSEP Focus: Clinical triage ethics; optimizing for asymmetric cost matrices (Recall/Sensitivity >= 97% over Accuracy), subgroup bias analysis, and clinical decision support safeguards.
Feedback Loop: Peer review guided visual layout of slides; verified cloud inference architecture and PACS integration parameters.
Unit 12: Continuous Deployment, MLOps & Post-Deployment Governance
Artefact: Architectural memo detailing cloud microservice deployment (AWS SageMaker / Triton), continuous Population Stability Index (PSI) drift monitoring, and clinical override audit logs.
LSEP Focus: Regulatory compliance under the EU AI Act (High-Risk Classification), post-market surveillance, and mandatory human-in-the-loop oversight.
Feedback Loop: Synthesized cohort discussion on automated model retraining triggers and clinical fallbacks.
2. Project Evolution: Final Implementation (Unit 11) vs. Initial Proposal (Unit 6)
The project underwent significant architectural and methodological maturation between the initial Unit 6 Proposal and the final Unit 11 System Implementation:

Dimension
Unit 6 Initial Proposal
Unit 11 Final Implementation
System Scope & Clinical Framing
Unconstrained, autonomous multi-class diagnostic tool attempting to differentiate viral, bacterial, fungal, and normal pediatric radiographs.
Objective, highly calibrated Tier-2 Clinical Decision Support Tool (Second Reader) for binary triage (Normal vs Pneumonia), augmented by diagnostic subgroup slicing across bacterial and viral manifestations.
Architectural Viability & Overfitting
Bespoke 8-layer deep convolutional network trained from scratch. Severe overfitting observed (>18% train-val divergence).
Transfer learning via ImageNet-pretrained ResNet-18 backbone with residual skip-connections, custom dropout (0.3), and AdamW regularisation. Benchmarked against classical deterministic baseline (HOG + intensity stats + RBF-SVM).
Data Integrity & Validation
Naive reliance on Kaggle's default folder partition (5,216 train / 16 val / 624 test) leading to high statistical variance.
Consolidated 80/10/10 Stratified Split maintaining class distributions. Stratified 5-Fold Cross-Validation on training distribution; 10% test set completely isolated until final reporting.
Explainability & Ethical Maturation
High-level, abstract discussion of GDPR and patient consent protocols.
Grounded empirical XAI: integrated Grad-CAM on final convolutional layer to visually verify pulmonary infiltrate focus over scanner artifacts. Evaluated via asymmetric cost matrix penalising False Negatives over False Positives.

3. Individual Contribution & Virtual Team Collaboration
3.1 Individual Technical Contributions
Deterministic Baseline Pipeline: Designed and implemented the hand-crafted feature extraction engine combining 8-orientation Histogram of Oriented Gradients (HOG) with first-order intensity statistics (mean, standard deviation, interquartile ranges).
PyTorch Deep Learning Pipeline: Architected the transfer learning pipeline, custom dataset classes, clinical data augmentations (rotation, jitter, horizontal flip), and class-imbalance correction via WeightedRandomSampler.
Explainability Architecture: Implemented forward and backward tensor hooks in PyTorch to compute Grad-CAM activation maps, generating visual overlay diagnostics on test samples.
Documentation & Reproducibility: Maintained repository structure, PEP8 compliance, pre-commit formatting, and structured notebook markdown for seamless team execution.
3.2 Virtual Teamwork & Dynamics
Role Alignment: Utilised Belbin's team role concepts, serving primarily as the technical implementer and monitor-evaluator, ensuring rigorous code validation.
Conflict Resolution & Consensus Building: When disagreements arose regarding model selection, technical friction was resolved through objective empirical sandboxing. Team members benchmarked competing proposals under identical stratified cross-validation conditions, creating consensus around the ResNet-18 architecture.
Asynchronous Collaboration: Managed sprint goals via GitHub Projects and issue tracking, conducting asynchronous pull-request code reviews to maintain repository stability.
4. Summative Reflective Piece
Context and the "What?" Stage
During this module, my technical focus centered on designing, benchmarking, and ethically evaluating machine learning systems under conditions of clinical risk and data uncertainty. Specifically, in Units 6 and 11, our team developed an end-to-end medical triage pipeline comparing a hand-crafted classical Support Vector Machine (SVM) against a deep residual convolutional network (ResNet-18) for pediatric pneumonia detection.

My primary technical responsibility was architecting the comparative evaluation framework. I constructed the feature engineering pipeline using Histogram of Oriented Gradients (HOG) paired with structural intensity statistics, implemented the PyTorch transfer learning model, and authored the Gradient-Weighted Class Activation Mapping (Grad-CAM) explainability scripts.

A critical incident occurred during mid-module testing: our deep learning model registered a misleadingly high validation accuracy of 96.8%. Rather than accepting this outcome, I audited the validation configuration. I discovered two fatal flaws: the original public dataset possessed an unbalanced validation holdout of only 16 scans, and the model was exhibiting shortcut learning by associating hospital positioning markers with pathology. Concurrently, our virtual team experienced friction regarding architectural direction: half the team favoured deploying a complex, uninterpretable Vision Transformer, while I advocated for a regularised ResNet-18 accompanied by deterministic baselines and robust explainability hooks. To resolve this, I established a standardized 80/10/10 stratified split, implemented 5-fold cross-validation, and ran an empirical benchmark proving that ResNet-18 achieved superior sensitivity (97.4%) with predictable convergence and visual interpretability.
Critical Analysis and the "So What?" Stage
This critical incident evoked intense frustration initially, followed by profound intellectual humility. Discovering that our initial "high-performing" model was exploiting background spatial artifacts highlighted the stark difference between academic benchmark chasing and real-world safety engineering. As Caruana et al. (2015) demonstrate in healthcare ML, high statistical accuracy frequently masks catastrophic reliance on confounders. Had this system been deployed in an active pediatric triage environment, those false correlations could have resulted in fatal misdiagnoses.

Working through this technical challenge forced me to critically examine my own cognitive biases. Earlier in the module, I operated under the assumption that deep neural architectures inherently superiorise classical methods across all operational contexts. However, evaluating our classical SVM baseline—which achieved an 86.4% accuracy using deterministic HOG descriptors—demonstrated that hand-crafted features offer structural transparency and low computational overhead that deep models cannot match natively. Nonetheless, the SVM failed clinically because it could not model non-linear, diffuse consolidations, registering an unacceptable 10.9% false-negative rate. In clinical triage, false negatives carry lethal consequences, whereas false positives result merely in secondary physician review. Thus, optimizing for Recall (Sensitivity greater than or equal to 97%) within an asymmetric cost matrix became our non-negotiable objective (Challen et al., 2019).

This realization directly influenced our virtual team dynamic. When resolving the dispute over model selection, I initially relied heavily on authoritative technical arguments. However, observing defensive reactions among team members made me realize that technical correctness does not substitute for collaborative leadership. Adopting Tuckman’s model of team development, I shifted my approach from argumentative persuasion to empirical demonstration. I set up an automated benchmarking notebook that enabled each team member to independently test and visualize their proposed models. This objective sandbox transformed interpersonal tension into collective technical inquiry. Furthermore, navigating our peer feedback loops taught me to value divergent perspectives: a peer's critique regarding subgroup vulnerability prompted our secondary analysis, which revealed that our model performed significantly worse on viral pneumonia (94.8% recall) than on bacterial consolidation (98.6% recall). This empirical disparity underscored how unaddressed dataset imbalances perpetuate algorithmic injustice (Buolamwini and Gebru, 2018).
Professional Impact and the "Now What?" Stage
The experiences gained across this module have fundamentally restructured my professional identity, moving me from a pure software engineering mindset toward rigorous, ethically grounded machine learning practice.

First, my technical mental model regarding machine learning algorithms has evolved. I no longer view algorithm selection as an isolated contest of predictive accuracy. Moving forward, I will enforce a mandatory evaluation triad in every machine learning deployment: empirical performance across asymmetric loss functions, computational stability under cross-validation, and explainability verification via attribution tools like Grad-CAM and SHAP (Lundberg and Lee, 2017). Whenever I encounter deep learning systems, I will proactively probe for shortcut learning, data leakage, and distributional shifts.

Second, this module transformed my approach to virtual team collaboration. In my professional capacity as an enterprise technology specialist, I routinely interface with cross-functional technical stakeholders. The friction experienced during Unit 6 taught me to establish objective, data-driven collaboration frameworks early. In future initiatives, I will immediately establish shared repository conventions, automated continuous integration tests, and structured decision matrices. This ensures that architectural debates are resolved through systematic empirical evidence rather than subjective assertion.

Finally, the ethical exploration of machine learning has permanently altered my design philosophy. The EU AI Act and clinical governance frameworks mandate that high-risk systems maintain human agency, data provenance, and post-market auditability (Jobin, Ienca and Vayena, 2019). I have internalized that machine learning models in safety-critical domains must never operate as autonomous decision-makers. Instead, they must be architected strictly as decision-support systems—acting as an intelligent "second reader" that elevates clinical efficiency while preserving human moral responsibility.

As an immediate personal action, I am translating these insights into my ongoing master's research and enterprise projects: integrating demographic slice auditing, population stability monitoring, and interpretability heatmaps into every predictive pipeline I deploy. Machine learning competence requires not just mathematical literacy, but the moral courage to hold algorithms accountable to the humans they are built to serve.
5. References
Buolamwini, J. and Gebru, T. (2018) 'Gender shades: Intersectional accuracy disparities in commercial gender classification', Proceedings of the 1st Conference on Fairness, Accountability and Transparency, PMLR, 81, pp. 77–91.
Caruana, R., Lou, Y., Gehrke, J., Koch, P., Sturm, M. and Elhadad, N. (2015) 'Intelligible models for healthcare: Predicting pneumonia risk and 30-day readmission', Proceedings of the 21th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pp. 1721–1730.
Challen, R., Denny, J., Pitt, M., Garside, L. and Edwards, T. (2019) 'Artificial intelligence, bias and clinical safety', BMJ Quality & Safety, 28(3), pp. 231–237.
Jobin, A., Ienca, M. and Vayena, E. (2019) 'The global landscape of AI ethics guidelines', Nature Machine Intelligence, 1(9), pp. 389–399.
Lundberg, S.M. and Lee, S.I. (2017) 'A unified approach to interpreting model predictions', Advances in Neural Information Processing Systems (NeurIPS), 30, pp. 4765–4774.
Rolfe, G., Freshwater, D. and Jasper, M. (2001) Critical reflection in nursing and the helping professions: a user’s guide. Basingstoke: Palgrave Macmillan.
