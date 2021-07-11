## Welcome Zombie_fly's dev website

这里将被用来存放个人项目（或所参与项目）的帮助文档

### 显示测试

以下部分作为简单的网页展示测试

```python
from json import loads, dump

class config():
    """配置文件管理
    """    
    def __init__(self, config_path: str) -> None:
        """配置文件操作初始化

        Args:
            config_path (str): 配置文件路径
        """        
        self.config_path= config_path
        self.read()
        return None
    def read(self) -> dict:
        """读取配置文件，转换为字典

        Returns:
            dict: 配置内容
        """
        
        with open(self.config_path,'r') as file_obj:
            text= file_obj.read()
        self.config= loads(text)
        return self.config
    def append(self, *args: dict) -> None:
        """配置追加
        
        Args:
            *args (dict): 追加内容
        """        
        for add_config in args:
            self.config.update(add_config)
        return
    def write(self) -> None:
        """以json形式写入配置文件至 self.config
        """        
        with open(self.config_path, 'w') as file_obj:
            dump(self.config, file_obj, indent=4, ensure_ascii=False)
        return
```

