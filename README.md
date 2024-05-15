# Minerva Workshop

This repository contains the materials for the Minerva Workshop. The workshop is designed to introduce Minerva platform with a hands-on experience. 
For this, we trained the SETR model using the F3 dataset for the task of facies clasification (i.e., semantic segmentation). 

The workshop is divided into two parts (three notebooks):
1. `1.minerva_setr_pup.ipynb`: This notebook introduces the Minerva platform and the SETR model. It also provides a hands-on experience on how to train the SETR model using the F3 dataset.
2. `2.minerva_setr_pup_pipeline.ipynb`: This notebook introduces the Minerva pipeline and how to use it to train the SETR model using the F3 dataset. Pipelines are a way to automate the training process and make it reproducible.
3. `3.minerva_cli.ipynb`: This notebook shows how to use the jsonargparse CLI to train the SETR model using the F3 dataset. Thus, we moved the `F3DataModule` and `Padding` classes to a separate file `example.py` and placed the configurations to the `config` directory, in order to allow the use of the CLI, in a pragmatic way.

The configurations are YAML files that define the data module, model, trainer, and pipeline. The configurations are organized in the following way:
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

In YAML files, `class_path` is used to specify the class path of the class that will be instantiated and `init_args` is used to specify the arguments that will be passed to the class constructor. Classes can be instantiated recursively, i.e., the `init_args` can contain other classes. All parameters for CLI must be passed as keyword arguments.
This architeture allows the user to easilly scale the configurations to more complex scenarios and, also, modularize the configurations.


## Requirements

- [Minerva installed](https://github.com/discovery-unicamp/Minerva) - we use the git version of Minerva,version 0.2.1-beta, at commit `353326d01ffc01ceefe9bfe659fdb48009e696dc` 
- F3 dataset (images and annotations) inside `f3` directory, in the root of this repository, with the following structure:
```
f3/
    images/
        train/
            il_0.tiff
            il_1.tiff
            ...
        val/
            il_0.tiff
            il_1.tiff
            ...
        test/
            il_0.tiff
            il_1.tiff
            ...
    annotations/
        train/
            il_0.png
            il_1.png
            ...
        val/
            il_0.png
            il_1.png
            ...
        test/
            il_0.png
            il_1.png
            ...
``` 

## License

This repository is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.