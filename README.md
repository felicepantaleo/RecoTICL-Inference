# Data for the CMSSW [RecoTICL/Inference](https://github.com/cms-sw/cmssw/tree/master/RecoTICL/Inference) package

The ONNX models that the TICL inference plugins read. The plugins are `TracksterInferenceByCNN`,
`TracksterInferenceByDNN` and `TracksterInferenceByPFN`. They run in pattern recognition, through
`TrackstersProducer`, and in linking, through `TracksterLinksProducer`.

The files are copies of the models in [cms-data/RecoHGCal-TICL](https://github.com/cms-data/RecoHGCal-TICL)
V00-10-00. The TICL code moved from `RecoHGCal/TICL` to the `RecoTICL` subsystem. The model content does
not change. `RecoHGCal-TICL` keeps its files for the older release cycles.

## Models

| File | Read by | Output |
|---|---|---|
| `CNN/patternrecognition/id_v0.onnx` | pattern recognition | particle identification probabilities |
| `CNN/linking/id_v0.onnx` | linking | particle identification probabilities |
| `DNN/patternrecognition/id_v0.onnx` | pattern recognition | particle identification probabilities |
| `DNN/patternrecognition/energy_v0.onnx` | pattern recognition | regressed energy |
| `DNN/linking/id_v0.onnx` | linking | particle identification probabilities |
| `DNN/linking/energy_v0.onnx` | linking | regressed energy |
| `PFN/patternrecognition/id_v0.onnx` | pattern recognition | particle identification probabilities |
| `PFN/patternrecognition/energy_v0.onnx` | pattern recognition | regressed energy |
| `PFN/linking/energy_v1.onnx` | linking | regressed energy |
| `PFN/linking/energy_v0.onnx` | the Phase-2 HLT menu | regressed energy |

The CNN and DNN models take an input tensor of `batch x 50 layers x 10 clusters x 3 features`. The PFN
models take `batch x 50 layers x 10 clusters x 7 features`. The identification output has 8 values, in
this order: photon, electron, muon, neutral pion, charged hadron, neutral hadron, ambiguous, unknown.
The energy output has one value, the trackster energy.
