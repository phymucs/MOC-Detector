# Actions as Moving Points

> Pytorch implementation of [Actions as Moving Points](https://arxiv.org/abs/2001.04608).
>
>  View each action instance as a trajectory of moving points.

<br/>

![image](image/Pipeline.jpg)

<br/>

# Abstract    

​	The existing action tubelet detectors mainly depend on heuristic anchor box design and placement, which might be computationally expensive and sub-optimal for precise localization of action instances. In this paper, we present a new action tubelet detection framework, termed as **MovingCenter Detector (MOC-detector)**, by treating an action instance as a trajectory of moving points. 

​    Based on the analysis that movement information could simplify and assist the action tubelet detection, our MOC-detector is decomposed into three crucial head branches:

- (1) Center Branch for in- stance center detection and action recognition.

- (2) Movement Branch for movement estimation at adjacent frames to form moving point trajectories.

- (3) Box Branch for spatial extent detection by directly regressing bounding box size at the estimated center point of each frame. 

​    These three branches work together to generate the tubelet detection results, that could be further linked to yield video level tubes with a common matching strategy. Our MOC-detector outperforms the existing state-of-the-art methods by a large margin under the same setting for frame-mAP and video-mAP on the JHMDB and UCF101-24 datasets. The performance gap is more evident for higher video IoU, demonstrating that our MOC-detector is particularly useful for more precise action detection.

<br/>

# Motivation

> Each action instance could be viewed as a trajectory of moving points. 

![image](image/Motivation.jpg)

​	In this view, action tubelet detector could be decomposed into three simple steps: 

- (1) localizing the center point (red dot) at key frame (i.e., center frame).
- (2) estimating the movement at each frame with respect to center point (yellow arrow).
- (3) regressing bounding box size at the calculated center point (green dots) for all frames. 

<br/>

# Illustration of Three Movement  Strategies

![image](image/Movement.jpg)

> *Left*: pipeline for detecting the bounding box at a non-key frame (i.e., normal frame).
>
> *Right*: illustration of detecting the tubelet.
>
> The arrow represents moving according to Movement Branch prediction, the red dot represents the key frame center and the green dot represents current frame center, which is localized by moving key frame center with Movement Branch prediction.

<br/>

![image](image/Movement_vis.jpg)

>Green box represents ground truth.
>
>Red box represents predicted box. 
>
>Note that the third frame is the key frame for tubelet length K=5.

<br/>

# Visualization


> Examples of Per-frame (K=1) and Tubelet (K=7) Detection.

![image](image/K_vision.jpg)

> Yellow color boxes present detection results.
>
>Yellow categories represent classifying correctly and red ones represent wrong. 
>
>Red dashed boxes represent missed actors.
>
> Green boxes and categories are the groundtruth.
>
>As our MOC-detector generates only one score and category for one tubelet, the score and category are only presented in the first frame for tubelet (K=7) detection.

<br/>



## Code will be released soon......

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>


### Citation
If you find this code is useful in your research, please cite:

```bibtex
@misc{li2020actions,
    title={Actions as Moving Points},
    author={Yixuan Li and Zixu Wang and Limin Wang and Gangshan Wu},
    year={2020},
    eprint={2001.04608},
    archivePrefix={arXiv},
    primaryClass={cs.CV}
}
```
