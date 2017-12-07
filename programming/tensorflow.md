## TensorFlow

### Install
#### OS X or Linux
Run the following command to set up the environment:  
```
conda create -n tensorflow python=3.6  
source activate tensorflow  
conda install pandas matplotlib jupyter notebook scipy scikit-learn  
pip install tensorflow
```

### Hello, world!
```python
import tensorflow as tf  

# create TensorFlow object called tensor  
hello_constant = tf.constant("Hello, world!")

with tf.Session() as sess:
    # Run the tf.constant operation in the session
    output = sess.run(hello_constant)
    print(output)
```

### Tensor
TensorFlowではデータはintegerやstringのような型を取らず、tensorオブジェクトを継承する。  
```python
hello_constant = tf.constant("Hello, world!")
```
は0次元のstring tensor。constantだから上書き不可。 


### Session
TensorFlow's api is build around the idea of a computational tgraph, a way of visualizing a mathematical progress.  
"A TensorFlow Session" is an environment for running a graph. The session is in charge of allocating the oprations to GPU(s) and/or CPU(s), including remote machines.  
The above code creates a session instance, *sess* using *tf.Session* .   
The *sess.run()* function then evaluates the tensor and returns the results.

### Input
#### tf.placeholder()
non-constantではない時に使う。
```python
x = tf.placeholder(tf.string)
y = tf.placeholder(tf.int32)
z = tf.placeholder(tf.float32)

with tf.Session() as sess:
    output = tf.run(x, feed_dict={x: 'Hello World', y: 132, z: 45.67})
```
tensor typeに合わないものを渡すとエラーが発生する。

### TensorFlow Math
```python
x = tf.add(1, 2) # 3
y = tf.subtract(5, 1) # 4
z = tf.multiply(3, 8) # 24
```

### Converting types
```python
tf.subtract(tf.cast(tf.constant(2.0), tf.int32), tf.constant(1)) # 1
```

### tf.Variable()
通常のPythonの変数と同じように書き換え可能。*tf.constant()*や*tf.placeholder()*は書き換え不可能。
```
x = tf.Variable(5)
```
`tf.Variable()`はsessionの中でstateを維持する。したがって、明示的にinitializeする必要がある。`tf.global_variables_initializer()`ですべての変数のstateをinitializeする。
```python
init = tf.global_variables_initializer()
with tf.Session() as sess:
    sess.run(init)
```


