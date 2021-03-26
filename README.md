# Reducing Commercial Aviation Fatalities

Pilots in commercial airlines have to manage several important tasks at once, like communication among crew or radio communication, programming the flight monitoring system, dealing with equipment malfunction and responding to abnormal situations. Even though they are well trained, it is in human nature to get distracted or panic under stress. However, if a pilot or the crew is not aware and recognise that he/she is in such a state, the safety of the passengers and the crew might be compromised. 

To solve this problem, Booz Allen Hamilton designed a kaggle challenge where physiological data of the pilots is provided and participants were asked to build a model to detect which one of the following states the pilot was in:

- **Channelized Attention(CA)** - This is the state when the pilot is completely focussed on one task, with no attention being paid to any other task
- **Diverted Attention(DA)** - This is the state when the pilot is being distracted by a secondary task, that requires some kind of decision making
- **Startled/Surprised(SS)** - This is the condition where the pilot is in a state of shock or panic when encountered with an abnormal situation
- **Baseline** - When the pilot is not experiencing any of the above conditions and is in a normal state.

In order to predict the above states physiological data of the pilots, who were subject to controlled experiments, collected in a non-flight environment, was provided in the training dataset. The test dataset consisted of physiological data of the pilots in a flight simulator, experiencing full flight. Each sensor operated at a sample rate of 256 Hz. The data consists of noise and artifacts as well.

## Data Fields

- **id** - Primary identifier of a sample, which is present in test dataset only
- **crew** - A unique id for a pair of pilots
- **experiment** - One of CA, DA, SS or LOFT. The first 3 comprise the training set. The latter the test set.
- **time** - seconds into the experiment
- **seat** - Indicator of whether the pilot is in left seat(0) or right seat(1)
- **eeg readings** - Electroencephalogram readings of pilot from 20 different electrodes namely eeg\_fp1, eeg\_f7, eeg\_f8, eeg\_t4, eeg\_t6, eeg\_t5, eeg\_t3, eeg\_fp2, eeg\_o1, eeg\_p3, eeg\_pz, eeg\_f3, eeg\_fz, eeg\_f4, eeg\_c4, eeg\_poz, eeg\_c3, eeg\_cz and eeg\_o2
- **ecg** - 3-point Electrocardiogram signal. The sensor had a resolution/bit of .012215 µV and a range of -100mV to +100mV. The data are provided in microvolts.
- **r** - Respiration, a measure of the rise and fall of the chest. The sensor had a resolution/bit of .2384186 µV and a range of -2.0V to +2.0V. The data are provided in microvolts.
- **gsr** - Galvanic Skin Response, a measure of electrodermal activity. The sensor had a resolution/bit of .2384186 µV and a range of -2.0V to +2.0V. The data are provided in microvolts.
- **event** - The state of the pilot at the given time: one of A = baseline, B = SS, C = CA, D = DA. Present only in the train dataset

## Performance metric

This is a multiclass classification problem, with the possibility of class imbalance as the events may not be uniformly distributed across time. Hence, the metric used here is Multiclass Log Loss
