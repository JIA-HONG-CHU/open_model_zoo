# human-pose-estimation-0002

## Use Case and High-Level Description

This is a multi-person 2D pose estimation network based on the EfficientHRNet approach (that follows the Associative Embedding framework).
For every person in an image, the network detects a human pose: a body skeleton consisting of keypoints and connections between them.
The pose may contain up to 17 keypoints: ears, eyes, nose, shoulders, elbows, wrists, hips, knees, and ankles.

## Example

![](./human-pose-estimation-0002.png)

## Specification

| Metric                          | Value                                     |
|---------------------------------|-------------------------------------------|
| Average Precision (AP)          | 44.4%                                     |
| GFlops                          | 5.9393                                    |
| MParams                         | 8.1504                                    |
| Source framework                | PyTorch\*                                  |

Average Precision metric described in [COCO Keypoint Evaluation site](https://cocodataset.org/#keypoints-eval).

## Inputs

Name: `input`, shape: [1x3x288x288]. An input image in the [BxCxHxW] format ,
where:
  - B - batch size
  - C - number of channels
  - H - image height
  - W - image width
Expected color order is BGR.

## Outputs

The net outputs three blobs:
  * "heatmaps" of shape [N, 17, 144, 144] containing location heatmaps for keypoints of all types.
  * "nms_heatmaps" of shape [N, 17, 144, 144] containing heatmaps after non-maximum suppression.
  * "embeddings" of shape [N, 17, 144, 144, 1] containing associative embedding values, which are used for grouping individual keypoints into poses.

## Legal Information
[*] Other names and brands may be claimed as the property of others.
