# china-address-code
国家统计局中国省市县乡村5级地址抓取，http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2018/index.html

使用已经抓取处理好的数据可以直接[下载](2018_addr.tsv.gz)。

## 数据格式说明

处理好的数据是tsv格式的文本文件，第一列是区划代码，第二列是地址名称。其中地址类型根据区划代码的位数进行区分：省级2位、市级4位、县级6位、乡级9位、村级12位。

## 抓取方式

通过[github.com/crawlerclub/bcrawler](https://github.com/crawlerclub/bcrawler)进行抓取。需要系统有Golang环境，然后执行如下命令安装bcrawler：

```sh
go get github.com/crawlerclub/bcrawler
```

bcrawler安装完成后，执行如下命令进行抓取：

```sh
# 每隔两秒钟抓取一次，爬虫配置文件在./conf目录，抓取的数据存储在./data目录
bcrawler -sleep 2 -log_dir ./log -alsologtostderr -conf ./conf
```

抓取完成后，执行如下命令进行数据处理：

```sh
python process.py > 2018_addr.tsv
#gzip 2018_addr.tsv
```

### 快速运行

```sh
git clone https://github.com/liuzl/china-address-code
cd china-address-code
./run.sh
```

## 抓取配置

抓取的配置文件都在`./conf/parsers`目录，每一个json文件对应着一类页面的抓取配置。