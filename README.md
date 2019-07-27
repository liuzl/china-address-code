# china-address-code
国家统计局中国省市县乡村5级地址抓取，http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2018/index.html

## 抓取方式

通过`github.com/crawlerclub/bcrawler`进行抓取。需要系统有Golang环境，然后执行如下命令安装bcrawler：

```sh
go get github.com/crawlerclub/bcrawler
```

bcrawler安装完成后，执行如下命令进行抓取：

```sh
# 每隔两秒钟抓取一次，爬虫配置文件在./conf目录，抓取的数据存储在./data目录
bcrawler -sleep 2 -log_dir ./log -alsologtostderr -conf ./conf
```

### 快速运行

```sh
git clone https://github.com/liuzl/china-address-code
cd china-address-code
./run.sh
```

## 抓取配置

抓取的配置文件都在`./conf/parsers`目录，每一个json文件对应着一类页面的抓取配置。