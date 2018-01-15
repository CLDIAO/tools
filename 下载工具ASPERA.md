# 安装

[Aspera下载]（http://downloads.asperasoft.com/） 下载合适系统的aspera connect

`bash aspera-connect-3.7.4.147727-linux-64.sh`

安装完成后目录中出现.aspera文件夹，有两个文件比较重要：①ascp的可执行文件：`~/.aspera/connect/bin/ascp`；②ascp的密钥文件：`~/.aspera/connect/etc/asperaweb_id_dsa.putty`。
  把ascp可执行文件的路径加入PATH变量中。`echo 'export PATH=~/.aspera/connect/bin:$PATH' >> ~/.bashrc`,`
source ~/.bashrc`

# 使用

执行命令时在最后加“.”,表示在当前目录。

## 从EBI下载：

在EBI页面里找到你想下载的文件，鼠标移动到ftp列，可以看到ftp地址，例如: ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR346/SRR346368/SRR346368.fastq.gz。
然后将ftp://ftp.sra.ebi.ac.uk 换成
era-fasp@fasp.sra.ebi.ac.uk即可
:`ascp -i ~/asperaweb_id_dsa.putty era-fasp@fasp.sra.ebi.ac.uk:/vol1/fastq/SRR346/SRR346368/SRR346368.fastq.gz`

参考格式：
`ascp -QT -l 300m -P33001 -i <aspera connect installation directory>/etc/asperaweb_id_dsa.openssh era-fasp@fasp.sra.ebi.ac.uk:<file or files to download> <download location>`

## 参考：

https://www.plob.org/article/3013.html

NCBI: https://www.ncbi.nlm.nih.gov/sra

EBI:https://www.ebi.ac.uk/ena/browse/read-download#downloading_files_ftp

http://bioinfostar.com/2017/12/23/How-to-download-SRA-data-zh_CN/
