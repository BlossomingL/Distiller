# 对distiller源码改动说明  
* distiller/apputils下的data_loaders.py文件classification_get_input_shape函数中dataset与yaml文件中dataset参数的值一样，例如：如果输入网络图像大小为80x80那么yaml文件中的dataset参数也就是80x80，如果需要添加其它类型的输入，那么就要更改此代码。
* distiller/policy.py下添加了fpgm的参数选项
* distiller/thinning.py下添加了两个个功能：
    * 能够剪PReLU层，具体函数为handle_prelu_layers，append_prelu_thinning_directive(注：如果PReLU层采用默认的参数1，那么需要将此代码注释掉，否则会出错)
    * 针对公司Block的第一层为BN层，源代码本身不支持对此层剪枝，更改后可支持。具体函数为handle_bn_layers_bn1。
* distiller/pruning/ranked_structures_pruner.py下添加了fpgm算法。具体代码为rank_and_prune_filters函数中if fpgm开始到if结束。
* distiller/summary_graph下更改源码一处BUG，在add_footprint_attr函数下加入try/catch模块
