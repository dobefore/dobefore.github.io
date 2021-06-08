---
title: python实用脚本
date: 2020-06-06 10:47:07
categories: 工具
tags:
- Python
- 脚本
---
# 1.调整图像尺寸/分辨率

### 1.需要安装的库

 `pip install PIL `

### 2.全部代码如下

```python
#修改源和目标图片目录
src_pic_dir=r'C:\Users\Admin\Desktop\qq'
dst_pic_dir=r'C:\Users\Admin\Desktop\background_pics'
from PIL import Image
import os
import glob
#修改为需要的目标尺寸
def convertjpg(jpgfile,outdir,width=700,height=500):
    img=Image.open(jpgfile)
    try:
        new_img=img.resize((width,height),Image.BILINEAR)   
        new_img.save(os.path.join(outdir,os.path.basename(jpgfile)))
    except Exception as e:
        print(e)
for jpgfile in os.listdir(src_pic_dir):
    os.chdir(src_pic_dir)
    if 'jpg' in jpgfile or 'png' in jpgfile:
        convertjpg(jpgfile,dst_pic_dir)
```

# 2.提取pdf(删除页数形成新的pdf)

### 1.需要安装的库

```
pip install PyPDF2
```

### 2.全部代码如下

```python
import os
from PyPDF2 import PdfFileWriter, PdfFileReader 
#下面这个list表示要保留的页码（通过设定页码重新生成相当于删过页面的新文件）
pages_to_keep = [i for i in range(8,83)] # page numbering starts from 0 
#pdf所在的文件夹
srcp='C:\\Users\\Admin\\Desktop\\python脚本\\文件操作\\pic'
os.chdir(srcp)
#pdf文件名
infile = PdfFileReader('python基础.pdf', 'rb') 
output = PdfFileWriter() 

for i in range(infile.getNumPages()): 
    if i in pages_to_keep: 
     p = infile.getPage(i) 
     output.addPage(p) 
#新pdf文件名
with open('newfile.pdf', 'wb') as f: 
    output.write(f) 
```

# 3.长图片裁剪成固定尺寸的图片

### 1.需要安装的库

```python
pip install PIL
```

```python
# 将这块代码存为py文件并与下面的代码文件在一个目录下
# 文件名 read_write_txt_list.py
def write_txt(txtfile,alist):
        filetxt=open(txtfile,'w',encoding='utf-8')
        for f in alist:
                
                filetxt.write(f)
                filetxt.write('\n')
        filetxt.close()

def txt_list(txtfile,listname):
        with open(txtfile, 'r',encoding='utf-8') as fd:
            for line in fd.readlines():
                #去掉txt里的‘nan’
                if not line.strip()=='nan':
                    lin=line.strip()
                    #listname.append(lin.strip('\ufeff'))
                    listname.append(lin.rstrip())
            return listname
def sweep(txtname):
        f=open(txtname, 'w+')
        f.truncate()
```

### 2.全部代码如下

```python
import os
from PIL import Image
from read_write_txt_list import write_txt,txt_list

def splitimage(lastdirname,aimdir):
    aim=os.path.join(aimdir,lastdirname)
    os.chdir(aim)
    for file in os.listdir(aim):
        img = Image.open(file)
        # w,h为宽度，和高度
        w,h = img.size
        height=w*(148/210)#A4纸比例出的高度（h/w）
        num=h/height+1#将分割出的图片数量
        index=0
        print(height)
        fn=os.path.splitext(file)
        bsname=fn[0]#文件名
        postfix=fn[-1]#后缀名
        #print('Original image info: %sx%s, %s, %s' % (w, h, img.format, img.mode)
        hei=[]
        write_txt('height.txt',str(height))
        txt_list('height.txt',hei)
        heis=float(''.join(hei))
        os.remove('height.txt')
        while (index < num):
            print('The index is:', index,"height is ",height)
            if index==0:
                box = (0, height-heis, w, height)
                img.crop(box).save(os.path.join(aim,str(index)+ '.' +bsname + postfix), img.format)
                height = height +heis
                index = index + 1
            else:
                box = (0, height-heis, w, height)
                img.crop(box).save(os.path.join(aim, str(index)+ postfix), img.format)
                height = height +heis
                index = index + 1
        os.remove(os.path.join(aim, str(index-1) + postfix))   
        os.remove(file)  
```

# 4.合并多个pdf文件

### 1.需要安装的库

```python
pip install PYPDF2
```

### 2.全部代码如下

```python
import os
from PyPDF2 import PdfFileReader, PdfFileWriter
import time
def timer(func):
    def wrapper(*args):
        time1 = time.time()
        func(*args)
        time2 = time.time()
        print('总共耗时：%s s.' %(time2 - time1))
    return wrapper

# 使用os模块的walk函数，搜索出指定目录下的全部PDF文件
# 获取同一目录下的所有PDF文件的绝对路径
def getFileName(filedir):

    file_list = [os.path.join(root, filespath) \
                 for root, dirs, files in os.walk(filedir) \
                 for filespath in files \
                 if str(filespath).endswith('pdf')
                 ]
    return file_list if file_list else []

# 合并同一目录下的所有PDF文件
@timer
def MergePDF(filepath, outfile):
    output = PdfFileWriter()
    outputPages = 0
    pdf_fileNames = getFileName(filepath)
    #先取出文件名的数字和对应的文件名做成dict，然后根据字典的key生成排好序的list
    q=filepath
    a=[]
    s={}
    d=[]
    pdf_fileName=[]
    for e in pdf_fileNames:
        a.append((os.path.split(e))[-1])
    for i in a:
        v=int(i.split('.')[0])
        s[v]=i
    for t in sorted(s.keys()):
        d.append(s[t])
    for e in d:
        pdf_fileName.append(q+'\\'+e)
    #pdf_fileName.sort()
    if pdf_fileName:
        for pdf_file in pdf_fileName:
            print("路径：%s"%pdf_file)
            # 读取源PDF文件
            input = PdfFileReader(open(pdf_file, "rb"))
            # 获得源PDF文件中页面总数
            pageCount = input.getNumPages()
            outputPages += pageCount
            print("页数：%d"%pageCount)
            # 分别将page添加到输出output中
            for iPage in range(pageCount):
                output.addPage(input.getPage(iPage))
            # 添加书签
            bookmarkname=os.path.split(pdf_file)[-1]
            output.addBookmark(title=bookmarkname[:-3], pagenum=outputPages - pageCount)
        print("合并后的总页数:%d."%outputPages)
        # 写入到目标PDF文件
        outputStream = open(os.path.join(filepath, outfile), "wb")
        output.write(outputStream)
        outputStream.close()
        print("PDF文件合并完成！")
    else:
        print("没有可以合并的PDF文件！")

# 主函数
def main(filedir,out_file):
    file_dir = filedir # 存放PDF的原文件夹(绝对路径)
    outfile =out_file # 输出的PDF文件的名称
    MergePDF(file_dir, outfile+'.pdf')
    
```

# 5.图片转pdf

### 1.需要安装的库

```
pip install PIL
```

### 2.全部代码如下

```python
# 图片转为pdf
from PIL import Image
import os
#需要在调用前明确指定工作目录在需要转为pdf图片的目录下os.chdir(dstdir)
def rea(pdf_name):
    #读取目录文件到list
    file_list = os.listdir(os.getcwd())
    pic_name = []
    im_list = []
    #把图片格式的文件名存在list
    for x in file_list:
        if os.path.splitext(x)[-1]=='.jpg':
            pic_name.append(x)
    #排序
    pic_name.sort()
    picname=pic_name
    #打开第一张图片
    im1=Image.open(pic_name[0])
    pic_name.pop(0)
    #循环打开并存储到pdf
    for i in pic_name:
        img = Image.open(i)
        # im_list.append(Image.open(i))
        if img.mode == "RGBA":
            img = img.convert('RGB')
            im_list.append(img)
        else:
            im_list.append(img)
    im1.save(pdf_name, "PDF", resolution=100.0, save_all=True, append_images=im_list)
    #删除图片
    for i in picname:
        os.remove(i)
    #给pdf文件加后缀名
    os.rename(pdf_name,pdf_name+'.pdf')
    #删除第一张图片
    for fi in os.listdir(os.getcwd()):
        if '.jpg' in fi:
            os.remove(fi)
    print("输出文件：", pdf_name+'.pdf')
```



