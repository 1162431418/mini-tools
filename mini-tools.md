# 小工具



## HuggingFace下载

以在 Enxin/MovieChat-1K_train 仓库下载 movies与jsons为例

### 准备工作

需要挂梯子，配置代理

安装对应的库

```shell
pip install hf_transfer 
pip install huggingface-hub      
```

导入环境变量，可加速

```shell
export HF_HUB_ENABLE_HF_TRANSFER=1
```

## 代码示例

```python
from huggingface_hub import hf_hub_download
from huggingface_hub import list_repo_files
# 指定仓库名称和文件名
repo_id = "Enxin/MovieChat-1K_train"
token = "114514"#替换为自己的
subfolder = "movies"


files = list_repo_files(repo_id=repo_id, repo_type="dataset",token = token)
# print(files)  # 输出所有文件名列表

# 下载文件并指定本地存放目录
for file in files:
    if file.endswith('.tar'):#因为只能获取所有文件列表，需要自行编写过滤的规则
        continue
    # print(file)
    file_path = hf_hub_download(repo_id=repo_id, filename=file, local_dir="/share/guanxuzeng/moviechat-1k",repo_type="dataset",token=token)#dataset需要指定 repo_type，默认是model
    
    print(f"{file} file downloaded to: {file_path}")
    # break
# print(f"{filename} file downloaded to: {file_path}")

```

