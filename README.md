## HorseFace

Horse face recognition. DASC2 course at Fontys.

To have the same environment [make sure your Virtual Environment (Venv) is active](README_VENV.md).

## Data
### Data source
[THoDBRL2015 Database](https://ieee-dataport.org/open-access/thodbrl2015-database)

### Data storage
Content of data folder is ignored in .gitignore

### Structure

    /data/THoDBRL2015/


## Databse Organisation

* Main Parts: The data is split into Part1, Part2, ..., Part5.

* Subfolders: Each part contains:
    * Base image: Presumably, base images of horses.
    * Cropped Images: Cropped versions of horse images.
    * videos: Contains folders named 1, 2, ..., corresponding to horse_id.

* Inside these folders:
    * Videos (e.g., 1V1.AVI, 1V2.AVI).
    * An images folder, which  contains stills.

## Dependencies
Keras 3 will be the default Keras version for TensorFlow 2.16 onwards. You may need to update your script to use Keras 3.