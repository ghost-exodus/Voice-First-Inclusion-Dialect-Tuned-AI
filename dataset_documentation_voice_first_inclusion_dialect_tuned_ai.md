# Dataset Documentation: Voice-First-Inclusion-Dialect-Tuned-AI

## 1. Overview

This dataset forms the empirical foundation for the **Voice-First-Inclusion-Dialect-Tuned-AI** project. It is specifically curated to capture the acoustic and lexical variations of the Hindi dialect spoken in the Ashta region of Madhya Pradesh, India (which exhibits strong morphological and phonetic influences from Malvi and Bhopali).

The primary objective of this dataset is to fine-tune end-to-end Automatic Speech Recognition (ASR) models for low-resource dialectal variations, mitigating the performance degradation typically observed when standard Hindi ASR systems encounter regional phonology and spontaneous local speech.

## 2. Methodology and Dataset Architecture

The dataset collection methodology strictly follows a tri-partite structure designed to elicit a comprehensive linguistic profile from each speaker. The design choices are grounded in established corpus linguistics and speech recognition engineering paradigms.

### 2.1. Part A: Scripted / Read Speech

Speakers read 42 phonetically balanced sentences in Devanagari. The sentences range from basic greetings to complex numerical strings, local geographical entities (e.g., Sehore, Kothri), and phonetic coverage matrices (aspirated vs. unaspirated, nasalizations).

* **Research Justification:** ASR models pre-trained on standardized text corpora require scripted speech to align acoustic boundaries effectively. Short sentence structures (8-15 words) minimize reading cognitive load, a methodology validated by large-scale Indic corpus studies to ensure higher acoustic fidelity among rural or non-expert readers. 

### 2.2. Part B: Extemporaneous / Spontaneous Speech

Speakers respond to tiered prompts (Daily Life, Everyday Life, Mother Tongue, and Free Talk) aimed at capturing 50-70 seconds of spontaneous speech per prompt.

* **Research Justification:** Spontaneous speech introduces severe word boundary alignment challenges due to variable articulation rates, hesitations, and dialect-specific syntax. Incorporating multi-tiered icebreaker questions prevents repetitive linguistic patterns and captures naturalistic co-articulation, which is critical for robust DNN-HMM and end-to-end ASR generalization.

### 2.3. Part C: Prompted Tasks and Entity Elicitation

This section focuses on isolated keywords (e.g., *mandi*, *soyabean*), local dialect candidate verification (e.g., *mhaaro*, *nakko*), tongue twisters, picture descriptions, and unscripted role-plays (e.g., bargaining with a shopkeeper).

* **Research Justification:** Foundational datasets in the Indic ASR domain utilize prompted tasks to elicit out-of-vocabulary (OOV) entities—such as specific dates, localized agricultural terms, and financial figures—that rarely occur organically in continuous free speech. Role-playing stimulates conversational dynamics, generating overlapping speech and dynamic pitch contours necessary for training conversational AI.

## 3. Technical Specifications

* **Audio Format:** Monophonic WAV.

* **Sampling Rate:** Minimum 16 kHz (44.1 kHz or 48 kHz preferred for high-fidelity feature extraction, such as Mel-Frequency Cepstral Coefficients (MFCCs)).

* **File Nomenclature:** `[SpeakerID]_[TaskID].wav` (e.g., `spk001_A01.wav`). Dual-speaker role-plays are annotated as `spk001-spk002_C41.wav`.

* **Transcription:** Transcription aligns with the spoken audio verbatim. Dialectal variations (e.g., uttering a Malvi synonym instead of the prompted Standard Hindi word) are retained and documented in the metadata to preserve acoustic-lexical integrity.

## 4. Ethical and Privacy Standards

Data collection adheres to strict data privacy protocols.

* **Anonymization:** Speaker identities are abstracted using unique alphanumeric identifiers (`spk001`, `spk002`).

* **Personally Identifiable Information (PII):** Speakers are explicitly instructed to avoid stating real names, addresses, or phone numbers. Any inadvertent PII captured during Part B (Spontaneous Speech) is flagged for post-processing redaction.

* **Consent:** Documented informed consent is mandatory prior to recording, adhering to institutional ethics guidelines for human-computer interaction studies.

## 5. Supporting Literature and Methodological References

The structural design, dialectal focus, and acoustic mapping of this dataset are directly supported by recent computational methodologies documented in IEEE and Springer:

1. **Dialectal Phonetic Variations in Madhya Pradesh:** 
   Our inclusion of localized prompts to capture specific regional phoneme shifts (such as the blurring of /s/ and /S/ sounds common in rural Madhya Pradesh) is supported by recent IEEE research on rural speech models. Accurate dataset curation mapping these exact pronunciation deviations is essential for lowering Word Error Rates (WER) in regional systems.
   * *Reference:* "A Voicebot with Pronunciation Feedback Mechanism for Rural India," *Proceedings of the 5th International Conference on Pervasive Computing and Social Networking (ICPCSN)*, IEEE, 2025. 
   * *Link:* [IEEE Xplore: 11035325](https://ieeexplore.ieee.org/document/11035325)

2. **Low-Resource Cross-Domain Speech Recognition:** 
   The tri-partite structure combining scripted, spontaneous, and entity-specific speech directly aids in few-shot prototype alignment for Indian domain gaps. Research out of VIT Bhopal demonstrates that robust feature modeling over domain-agnostic rural representations (like the Ashta dialect) heavily relies on the type of varied acoustic data generated in Parts A and B of this dataset.
   * *Reference:* O. V. Sawant and A. Bhowmick, "Bridging Domain Gaps With ProtoAlign: Teacher–Student Few-Shot Prototype Alignment for Cross-Domain Spoken Language Recognition," *IEEE Access*, vol. 14, 2026. 
   * *Link:* [IEEE Xplore: 11346933](https://ieeexplore.ieee.org/document/11346933)

3. **Code-Mixed and Code-Switched Entity Elicitation:** 
   Part C of the dataset (entity elicitation and English loanwords like *mobile*, *recharge*, *parking*) addresses the acoustic challenges of code-mixed Indic languages. Springer research emphasizes that isolating Code-Switched (CS) terms in low-resource environments prevents end-to-end models from heavily penalizing OOV tokens during continuous speech decoding.
   * *Reference:* "Comparative performance analysis of end-to-end ASR models on Code Switched and Code Mixed Speech Recognition for Indic Languages," *Springer*, 2025. 
   * *Link:* [Springer Link: 10.1186/s13636-025-00395-5](https://link.springer.com/content/pdf/10.1186/s13636-025-00395-5.pdf)