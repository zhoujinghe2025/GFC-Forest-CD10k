# Literature Positioning Notes

## Why GFC-Forest-CD10k is distinct

Most widely used change detection benchmarks focus on urban or building changes, high-resolution optical image pairs, or generic land-cover changes. GFC-Forest-CD10k is positioned differently: it targets forest change detection, uses GFC-derived forest-loss supervision, includes an explicit ignore mask, and emphasizes multi-region forest contexts.

## Comparison anchors

- LEVIR-CD is a classic high-resolution building change benchmark with 637 image pairs of 1024 x 1024 pixels at 0.5 m resolution, collected from 20 Texas regions.
- OpenMapCD is a recent multimodal optical-map change detection benchmark with 1288 samples of 1024 x 1024 pixels from 40 regions across six continents and additional OOD areas in Japan.
- OpenEarthMap is not a change detection dataset, but it is useful as a global remote-sensing benchmark reference because it emphasizes multi-country and multi-continent coverage with manual land-cover labels.

## Manuscript angle

The strongest publishable claim should not be that GFC-Forest-CD10k is larger than every existing dataset. Instead, the claim should be that it provides a fixed, ignore-mask-aware, multi-regional benchmark for forest change detection with reproducible GFC-derived labels, controlled positive/negative sampling, and region-wise evaluation protocols.

## Claims to avoid until human audit and baselines are complete

- Do not claim manually verified dense labels.
- Do not claim state-of-the-art model performance.
- Do not claim global representativeness without a stronger biome/continent sampling analysis.
- Do not claim final benchmark status until release version, license, checksums, and baseline results are frozen.
