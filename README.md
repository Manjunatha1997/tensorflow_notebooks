# tensorflow_notebooks

# Tensorflow version2 (Copy_of_tf2_object_detection)
# steps for Tensorflow 2

Step1:
=======
We have to mount the google drive

Step2:
======
We have to check the version as %tensorflow_version 2.X

Step3:
======
We have to change the directory to research folder for this follow below command.
%cd /content/drive/MyDrive/tf2/models/research

Then we have to run the following commands like below
!python setup.py build
!python setup.py install

Step4:
======
We have to change the directory to slim which is insode research folder for this use below command
%cd /content/drive/MyDrive/tf2/models/research/slim

Then we have to run the following commands like below
!python setup.py build
!python setup.py install

Step5:
======
We have to change the directory to research folder , for this use below command
%cd /content/drive/MyDrive/tf2/models/research

Then we have to run the following command
!protoc --python_out=. ./object_detection/protos/anchor_generator.proto ./object_detection/protos/argmax_matcher.proto ./object_detection/protos/bipartite_matcher.proto ./object_detection/protos/box_coder.proto ./object_detection/protos/box_predictor.proto ./object_detection/protos/eval.proto ./object_detection/protos/faster_rcnn.proto ./object_detection/protos/faster_rcnn_box_coder.proto ./object_detection/protos/grid_anchor_generator.proto ./object_detection/protos/hyperparams.proto ./object_detection/protos/image_resizer.proto ./object_detection/protos/input_reader.proto ./object_detection/protos/losses.proto ./object_detection/protos/matcher.proto ./object_detection/protos/mean_stddev_box_coder.proto ./object_detection/protos/model.proto ./object_detection/protos/optimizer.proto ./object_detection/protos/pipeline.proto ./object_detection/protos/post_processing.proto ./object_detection/protos/preprocessor.proto ./object_detection/protos/region_similarity_calculator.proto ./object_detection/protos/square_box_coder.proto ./object_detection/protos/ssd.proto ./object_detection/protos/ssd_anchor_generator.proto ./object_detection/protos/string_int_label_map.proto ./object_detection/protos/train.proto ./object_detection/protos/keypoint_box_coder.proto ./object_detection/protos/multiscale_anchor_generator.proto ./object_detection/protos/graph_rewriter.proto ./object_detection/protos/calibration.proto ./object_detection/protos/flexible_grid_anchor_generator.proto


Step6:
======
We have to change the diredctyory to object_detection folder, for this use below command
%cd /content/drive/MyDrive/tf2/models/research/object_detection

Then we have to run the followig command 








