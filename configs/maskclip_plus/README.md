# MaskCLIP: Extract Free Dense Labels from CLIP

## Abstract
<!-- [ABSTRACT] -->
Contrastive Language-Image Pre-training (CLIP) has made a remarkable breakthrough in open-vocabulary zero-shot image recognition. Many recent studies leverage the pre-trained CLIP models for image-level classification and manipulation. In this paper, we wish examine the intrinsic potential of CLIP for pixel-level dense prediction, specifically in semantic segmentation. To this end, with minimal modification, we show that MaskCLIP yields compelling segmentation results on open concepts across various datasets in the absence of annotations and fine-tuning. By adding pseudo labeling and self-training, MaskCLIP+ surpasses SOTA transductive zero-shot semantic segmentation methods by large margins, e.g., mIoUs of unseen classes on PASCAL VOC/PASCAL Context/COCO Stuff are improved from 35.6/20.7/30.3 to 86.1/66.7/54.7. We also test the robustness of MaskCLIP under input corruption and evaluate its capability in discriminating fine-grained objects and novel concepts. Our finding suggests that MaskCLIP can serve as a new reliable source of supervision for dense prediction tasks to achieve annotation-free segmentation.

## Results and models of annotation-free segmentation

#### Pascal VOC 2012 + Aug (w/o Background)

| Method     | CLIP Model | Target Model          | Crop Size | Lr schd | mIoU | config                                                                               |
| ---------- | ---------- | --------------------- | --------- | --------|----: | -------------------------------------------------------------------------------------|
| MaskCLIP+ | R-50       | DeepLabv2-R-101-d8    | 512x512   | 2000    | 58.4 | [config](anno_free/maskclip_plus_r50_deeplabv2_r101-d8_512x512_2k_voc12aug_20.py)   |
| MaskCLIP+ | R-50x16    | DeepLabv2-R-101-d8    | 512x512   | 2000    | 67.5 | [config](anno_free/maskclip_plus_r50x16_deeplabv2_r101-d8_512x512_2k_voc12aug_20.py)|


#### Pascal Context (w/o Background)

| Method     | CLIP Model | Target Model          | Crop Size | Lr schd | mIoU | config                                                                                     |
| ---------- | ---------- | --------------------- | --------- | --------|----: | -------------------------------------------------------------------------------------------|
| MaskCLIP+ | R-50       | DeepLabv2-R-101-d8    | 480x480   | 4000    | 23.9 | [config](anno_free/maskclip_plus_r50_deeplabv2_r101-d8_480x480_4k_pascal_context_59.py)   |
| MaskCLIP+ | R-50x16    | DeepLabv2-R-101-d8    | 480x480   | 4000    | 25.1 | [config](anno_free/maskclip_plus_r50x16_deeplabv2_r101-d8_480x480_4k_pascal_context_59.py)|
| MaskCLIP+ | ViT-B/16   | DeepLabv2-R-101-d8    | 480x480   | 4000    | 31.1 | [config](anno_free/maskclip_plus_vit16_deeplabv2_r101-d8_480x480_4k_pascal_context_59.py)|


#### COCO-Stuff 164k

| Method     | CLIP Model | Target Model          | Crop Size | Lr schd | mIoU | config                                                                                  |
| ---------- | ---------- | --------------------- | --------- | --------|----: | ----------------------------------------------------------------------------------------|
| MaskCLIP+ | R-50       | DeepLabv2-R-101-d8    | 512x512   | 8000    | 13.6 | [config](anno_free/maskclip_plus_r50_deeplabv2_r101-d8_512x512_8k_coco-stuff164k.py)   |
| MaskCLIP+ | R-50x16    | DeepLabv2-R-101-d8    | 512x512   | 8000    | 17.6 | [config](anno_free/maskclip_plus_r50x16_deeplabv2_r101-d8_512x512_8k_coco-stuff164k.py)|
| MaskCLIP+ | ViT-B/16   | DeepLabv2-R-101-d8    | 512x512   | 8000    | 18.0 | [config](anno_free/maskclip_plus_vit16_deeplabv2_r101-d8_512x512_8k_coco-stuff164k.py)|


## Results and models of zero-shot segmentation

#### Pascal VOC 2012 + Aug (w/o Background)

| Method     | CLIP Model | Target Model          | Crop Size | Lr schd | mIoU | config                                                                                |
| ---------- | ---------- | --------------------- | --------- | --------|----: | --------------------------------------------------------------------------------------|
| MaskCLIP+ | R-50       | DeepLabv2-R-101-d8    | 512x512   | 20000   | 88.1 | [config](zero_shot/maskclip_plus_r50_deeplabv2_r101-d8_512x512_20k_voc12aug_20.py)   |


#### Pascal Context

| Method     | CLIP Model | Target Model           | Crop Size | Lr schd | mIoU | config                                                                                      |
| ---------- | ---------- | ---------------------- | --------- | --------|----: | --------------------------------------------------------------------------------------------|
| MaskCLIP+ | R-50       | DeepLabv3+-R-101-d8    | 480x480   | 40000   | 48.1 | [config](zero_shot/maskclip_plus_r50_deeplabv2_r101-d8_480x480_40k_pascal_context_59.py)   |


#### COCO-Stuff 164k

| Method     | CLIP Model | Target Model          | Crop Size | Lr schd | mIoU | config                                                                                   |
| ---------- | ---------- | --------------------- | --------- | --------|----: | -----------------------------------------------------------------------------------------|
| MaskCLIP+ | R-50       | DeepLabv2-R-101-d8    | 512x512   | 80000   | 39.6 | [config](zero_shot/maskclip_plus_r50_deeplabv2_r101-d8_512x512_80k_coco-stuff164k.py)   |