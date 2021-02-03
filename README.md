
# tensorflow_notebooks

# Tensorflow version2 (Copy_of_tf2_object_detection)
# steps for Tensorflow 2

Step1:
=======
==> You have to mount the google drive

Step2:
======
==> You have to select the version as 
%tensorflow_version 2.X

Step3:
======
==> You have to change the directory to research folder for this follow below command.
%cd /content/drive/MyDrive/tf2/models/research

==> Then You have to run the following commands like below
!python setup.py build
!python setup.py install

Step4:
======
==> You have to change the directory to slim which is insode research folder for this use below command
%cd /content/drive/MyDrive/tf2/models/research/slim

==> Then You have to run the following commands like below
!python setup.py build
!python setup.py install

Step5:
======
==> You have to change the directory to research folder , for this use below command
%cd /content/drive/MyDrive/tf2/models/research

==> Then You have to run the following command
!protoc --python_out=. ./object_detection/protos/anchor_generator.proto ./object_detection/protos/argmax_matcher.proto ./object_detection/protos/bipartite_matcher.proto ./object_detection/protos/box_coder.proto ./object_detection/protos/box_predictor.proto ./object_detection/protos/eval.proto ./object_detection/protos/faster_rcnn.proto ./object_detection/protos/faster_rcnn_box_coder.proto ./object_detection/protos/grid_anchor_generator.proto ./object_detection/protos/hyperparams.proto ./object_detection/protos/image_resizer.proto ./object_detection/protos/input_reader.proto ./object_detection/protos/losses.proto ./object_detection/protos/matcher.proto ./object_detection/protos/mean_stddev_box_coder.proto ./object_detection/protos/model.proto ./object_detection/protos/optimizer.proto ./object_detection/protos/pipeline.proto ./object_detection/protos/post_processing.proto ./object_detection/protos/preprocessor.proto ./object_detection/protos/region_similarity_calculator.proto ./object_detection/protos/square_box_coder.proto ./object_detection/protos/ssd.proto ./object_detection/protos/ssd_anchor_generator.proto ./object_detection/protos/string_int_label_map.proto ./object_detection/protos/train.proto ./object_detection/protos/keypoint_box_coder.proto ./object_detection/protos/multiscale_anchor_generator.proto ./object_detection/protos/graph_rewriter.proto ./object_detection/protos/calibration.proto ./object_detection/protos/flexible_grid_anchor_generator.proto


Step6:
======

==> You have to split the dataset into test and train folders and you have to push the folders into images folder

==> You have to change the directory to object_detection folder, for this use below command
%cd /content/drive/MyDrive/tf2/models/research/object_detection

==> Then You have to run the followig command 
!python xml_to_csv.py

Step7:
======

==> You have to change the directory to object_detection folder
==> Open generate_tfrecord.py file and there you need to edit the classnames according to your classnames which is you can find in class_text_to_int function in that file.
==> Then run the following commands,which will create a train.record and test.record files

!python generate_tfrecord.py --csv_input=images/train_labels.csv --image_dir=images/train --output_path=train.record
!python generate_tfrecord.py --csv_input=images/test_labels.csv  --image_dir=images/test --output_path=test.record


Step8:
======
==> Open faster_rcnn_resnet152_v1_800x1333_coco17_gpu-8.config file which is you can find in training folder
==> Edit the file according to your dataset like
1. num_classes 
2. num_steps 
3. fine_tune_checkpoint
4. label_map_path
5. input_path
6. label_map_path
7. input_path

==> Open the labelmap.pbtxt and edit the file according to your dataset
==> Then run the following command for training the data.
!python model_main_tf2.py --model_dir=training --pipeline_config_path=training/faster_rcnn_resnet152_v1_800x1333_coco17_gpu-8.config --alsologtostderr

Step9:
=====
==> Change the directory to object_detection folder
==> You need to export the inference_graph for this, use below command
!python exporter_main_v2.py --trained_checkpoint_dir=training --output_directory=inference_graph --pipeline_config_path=training/faster_rcnn_resnet152_v1_800x1333_coco17_gpu-8.config

==> It will created inference_graph folder

Step10:
======
==> You need to creat a folder called 'test_result', and the folder should be same.
==> You need to test the data , for this open Object_detection_image.py file which is in object_detection folder and you need to edit over the path that is your test folder path over the 
for imgs in glob.glob("/home/lincode/tensorflow2/models/research/object_detection/images/test/*.jpg"): line.
==> You need to change the directory to object_detection folder
==> Then run the following command for testing your data.
!python Object_detection_image.py

