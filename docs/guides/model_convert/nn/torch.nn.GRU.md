## torch.nn.GRU
### [torch.nn.GRU](https://pytorch.org/docs/stable/generated/torch.nn.GRU.html?highlight=torch%20nn%20gru#torch.nn.GRU)
```python
torch.nn.GRU(input_size,
             hidden_size,
             num_layers=1,
             bias=True,
             batch_first=False,
             dropout=0,
             bidirectional=False)
```

### [paddle.nn.GRU](https://www.paddlepaddle.org.cn/documentation/docs/zh/api/paddle/nn/GRU_cn.html#gru)
```python
paddle.nn.GRU(input_size,
              hidden_size,
              num_layers=1,
              direction='forward',
              dropout=0.,
              time_major=False,
              weight_ih_attr=None,
              weight_hh_attr=None,
              bias_ih_attr=None,
              bias_hh_attr=None)
```

两者功能一致但参数不一致，部分参数名不同，具体如下：
### 参数差异
| PyTorch       | PaddlePaddle | 备注                                                   |
| ------------- | ------------ | ------------------------------------------------------ |
| bias          | -            | 表示 LSTM 后将映射到对应的大小，PaddlePaddle 无此功能。  |
| batch_first   | time_major   | PyTorch 表示 batch size 是否为第一维，PaddlePaddle 表示 time steps 是否为第一位，它们的意义相反。  |
| bidirectional | direction    | PyTorch 表示是否进行双向 LSTM，PyTorch 使用字符串表示是双向 LSTM（`bidirectional`）还是单向 LSTM（`forward`）。 |
| -             |weight_ih_attr| weight_ih 的参数。  |
| -             |weight_hh_attr| weight_hh 的参数。  |
| -             | bias_ih_attr | bias_ih 的参数。  |
| -             | bias_hh_attr | bias_hh 的参数。  |

### 转写示例
#### bias：是否使用偏置
```python
# Pytorch 写法
torch.nn.GRU(16, 32, bias=True)

# Paddle 写法
paddle.nn.GRU(16, 32)
```
```python
# Pytorch 写法
torch.nn.GRU(16, 32, bias=False)

# Paddle 写法
paddle.nn.GRU(16, 32, bias_ih_attr=False, bias_hh_attr=False)
```

#### batch_first：batch size 是否为第一维
```python
# Pytorch 写法
torch.nn.GRU(16, 32, batch_first=True)

# Paddle 写法
paddle.nn.GRU(16, 32, time_major=False)
```

#### bidirectional：是否进行双向
```python
# Pytorch 写法
torch.nn.GRU(16, 32, bidirectional=True)

# Paddle 写法
paddle.nn.GRU(16, 32, direction='bidirectional')
```
```python
# Pytorch 写法
torch.nn.GRU(16, 32, bidirectional=False)

# Paddle 写法
paddle.nn.GRU(16, 32, direction='forward')
```
