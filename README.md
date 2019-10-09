<p align="center"><img width=500 src="/docs/docs/img/sotabencheval.png"></p>

--------------------------------------------------------------------------------

[![PyPI version](https://badge.fury.io/py/sotabencheval.svg)](https://badge.fury.io/py/sotabencheval) [![Generic badge](https://img.shields.io/badge/Documentation-Here-<COLOR>.svg)](https://shields.io/)

`sotabencheval` is a framework-agnostic library that contains a collection of deep learning benchmarks you can use to benchmark your models. It can be used in conjunction with the [sotabench](https://www.sotabench.com) service to record results for models, so the community can compare model performance on different tasks, as well as a continuous integration style service for your repository to benchmark your models on each commit.

## Benchmarks Supported

- [ADE20K](https://paperswithcode.github.io/sotabench-eval/ade20k/) (Semantic Segmentation)
- [COCO](https://paperswithcode.github.io/sotabench-eval/coco/) (Object Detection)
- [ImageNet](https://paperswithcode.github.io/sotabench-eval/imagenet/) (Image Classification)
- [SQuAD](https://paperswithcode.github.io/sotabench-eval/squad/) (Question Answering)
- [WikiText-103](https://paperswithcode.github.io/sotabench-eval/wikitext-103/) (Language Modelling)
- [WMT](https://paperswithcode.github.io/sotabench-eval/wmt/) (Machine Translation)

PRs welcome for further benchmarks! 

## Installation

Requires Python 3.6+. 

```bash
pip install sotabench-eval
```

## Get Benching! 🏋️

You should read the [full documentation here](https://paperswithcode.github.io/sotabench-eval/index.html), which contains guidance on getting started and connecting to [sotabench](https://www.sotabench.com).

Integration is lightweight. For example, if you are evaluating an ImageNet model, you initialize an Evaluator object and (optionally) link to the paper where the model originated from to compare with published results:

```
from sotabencheval.image_classification import ImageNetEvaluator

evaluator = ImageNetEvaluator(
             model_name='ResNeXt-101-32x8d',
             paper_arxiv_id='1611.05431')
```

Then for each batch of predictions your model makes on ImageNet, you pass a dictionary of keys as image IDs and values as output predictions to the `evaluator.add` method:

```
evaluator.add(dict(zip(image_ids, batch_output)))
```

This logic just needs to be written in a `sotabench.py` file (which contains whatever evaluation logic you need - e.g loading and processing the data), and sotabench will run it on each commit and record the results:

[]


## Contributing

All contributions welcome!



