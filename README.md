# Minerva Workshop

This repository contains the materials for the Minerva Workshop, which is designed to introduce the Minerva platform through hands-on experience. 
For this workshop, we trained the SETR model using the F3 dataset for the task of facies classification (i.e., semantic segmentation).

The workshop is divided into two parts (three notebooks):

1. `1.minerva_setr_pup.ipynb`: This notebook introduces the Minerva platform and the SETR model. It also provides hands-on experience on how to train the SETR model using the F3 dataset.
2. `2.minerva_setr_pup_pipeline.ipynb`: This notebook introduces the Minerva pipeline and demonstrates how to use it to train the SETR model with the F3 dataset. Pipelines automate the training process and ensure reproducibility.
3. `3.minerva_cli.ipynb`: This notebook shows how to use the `jsonargparse` CLI to train the SETR model with the F3 dataset. To facilitate this, we moved the `F3DataModule` and `Padding` classes to a separate file (`example.py`) and placed the configurations in the `config` directory, enabling practical CLI usage.

The configurations are YAML files that define the data module, model, trainer, and pipeline. They are organized as follows:
```
configs/
    data_module/
        f3.yaml
    model/
        setr_pup.yaml
    pipelines/
        lightning_pipeline/
            setr_pup_f3_train.yaml
    trainer/
        default.yaml
```

In the YAML files, `class_path` specifies the class path of the class to be instantiated, and `init_args` specifies the arguments to be passed to the class constructor. Classes can be instantiated recursively, meaning that `init_args` can contain other classes. All parameters for the CLI must be passed as keyword arguments. This architecture allows users to easily scale configurations to more complex scenarios and modularize the configurations.

## Requirements

- [Minerva installed](https://github.com/discovery-unicamp/Minerva) - We use the git version of Minerva, version `0.2.1-beta` (commit `353326d01ffc01ceefe9bfe659fdb48009e696dc`).
- [F3 dataset](https://arxiv.org/pdf/1904.00770) (images and annotations) placed inside the `f3` directory in the root of this repository, with the following structure:
```
f3/
    images/
        train/
            0.tiff
            1.tiff
            ...
        val/
            0.tiff
            1.tiff
            ...
        test/
            0.tiff
            1.tiff
            ...
    annotations/
        train/
            0.png
            1.png
            ...
        val/
            0.png
            1.png
            ...
        test/
            0.png
            1.png
            ...
```

## License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
