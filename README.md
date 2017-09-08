# data base
SINCE THE TUNED MODEL IS TOO BIG I DIDN'T PUT THEM IN THE FOLDER!!
So please first create a folder in current path named `lfw_funneled`. Then download the lfw_funneled data and put it in `lfw_funneled` folder.

# run
Please first change your current path to the `src` folder.
1. draw alex net
> python draw_net.py ./alex/deploy.prototxt ./tmp/alex.png
2. test untrained Alex net with ../lfw_funneled data
> python alex_test.py 

3. generate lmdb
> python generateLmdb.py

4. train alex net:
> cd ~/Desktop/ongoing/DLProj2/src
>/home/hua/Programs/caffe/build/tools/caffe train -solver /home/hua/Desktop/ongoing/DLProj2/src/alex_ft/solver.prototxt -weights /home/hua/Desktop/ongoing/DLProj2/src/alex_ft/alex_ft_init.caffemodel -gpu 0
5. rename the trained snapshot to alex_ft_trained.caffemodel
6. seperate :
> python alex_seperate.py
7. test trained Alex
> python alex_test.py

8. train vgg net:
> cd ~/Desktop/ongoing/DLProj2/src
>/home/hua/Programs/caffe/build/tools/caffe train -solver /home/hua/Desktop/ongoing/DLProj2/src/vgg16_ft/solver.prototxt -weights /home/hua/Desktop/ongoing/DLProj2/src/vgg16_ft/vgg_ft_init.caffemodel -gpu 0
9. rename the trained snapshot to vgg_ft_trained.caffemodel
10. seperate :
> python vgg_seperate.py
11. test trained VGG
> python vgg_test.py

# For more info:
* [paper](https://github.com/hualiu01/FinetuneDNN/blob/master/report.pdf)
