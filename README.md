###################
这是什么
###################
仿照Cache写的一个锁 driver，暂未考虑多机分布式。

*******************
如何使用
*******************

1. 拷贝整个Lock文件夹到你的 application/libraries 文件夹下。
2. 根据需要调用不同的锁类型。暂时只有文件和redis，之后慢慢增加其他类型。

- 文件  
在 application/config.php 文件中新增一项配置，锁存放文件夹  
    $config['lock_path'] = 'XXX';  
使用：  
    $this->load->driver('lock', array('adapter' => 'file', 'key_prefix' => ''));  
    $this->lock->lock('test');  
    //你自己的处理代码  
    $this->lock->unlock('test');  

- redis  
默认使用系统的redis配置，可自行修改Lock_redis.php中代码。  
使用：  
    $this->load->driver('lock', array('adapter' => 'redis', 'key_prefix' => ''));  
    $this->lock->lock('test', 10); //第二个参数为超时时间  
    //你自己的处理代码  
    $this->lock->unlock('test');  
