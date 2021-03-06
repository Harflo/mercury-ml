# History

## 0.2.3 
- Custom __str__ functions have been added to DataSet and DataBuch so that printing instances of these will show a sensible hierarchy of information
- A generic "read_data_bunch" function has been added to mercury_ml.common.tasks which can take arbitrarily named DataSets
- The `read_pandas_data_set` function in `mercury_ml.common.source_reading.disk` has been made more abstract. It can will now create arbitrarily named data_wrappers based on what is input in the `data_wrappers_params` field

## 0.2.2
- Saving to S3 now always overwrites as the methods used so far to check whether an object exists has proven to be less than reliable

## 0.2.1
- Fixed a small error where checking whether a S3 object already exists did not work correctly

## 0.2.0
- This release sees the introduction to TensorFlow 2.0, for now using the pre-release alpha version. The `keras` implementations have all been replaced with `tensorflow.keras`.
- It is now also possible to save models using the tensorflow saved_model API
- The "providers" / "containers" structure has been flattened. Modules that were previously under `mercury_ml.common.providers` and under `mercury_ml.common.containers` are now simply under `mercury_ml.common`. The same goes for the structure under `mercury_ml.<machine learning engine>`

## 0.1.4
- Under `mercury_ml.keras.providers.model_fitting` bot `fit` and `fit_generator` now:
  1. Accept `**kwargs` to be passed to the underlying Keras functions
  2. If `save_best_model=True` will only reload model weights (instead of importing an entire model as was done before). This keeps model training history intact

## 0.1.3
- MongoDBSingleton now only imports pymongo from within the __init__ scope
- saving artifacts to MongoDB will now correctly update only the lowest level the the document_key provided)
- copying from s3 to disk will now automatically create the local directory to be downloaded to

## 0.1.2
- It is now possible to store dictionary artifacts to MongoDB

## 0.1.1

- Keras Model fitting methods at `mercury_ml.keras.providers.model_fitting` now allow for keyboard interrupts (either last, or last_best model will be returned)
- `mercury_ml.common.utils.recursively_update_config` will now correctly iterate through both dictionaries and lists
- In `mercury_ml.common.artifact_copying.from_disk.copy_from_disk_to_s3` it is now possible to specify whether or not an existing S3 file should be overwritten 
- A `copy_from_s3_to_s3` method has been added `mercury_ml.common.artifact_copying.from_s3`

## 0.1.0

Initial (pre-release) version. Most currently functionality has been tested and works. Lot's of functionality still to come.
Only Keras and H2O currently supported, but the aim is to eventually support all major (and some minor) machine learning
frameworks.