# embodied-intelligence
Learn the open-source courses of DataWhale
  habitat-sim环境搭建
    1.创建conda环境(先创建一个虚拟环境）
      conda create -n habitat python=3.9 cmake=3.14.0
      conda activate habitat
    2.在自己的电脑上运行或者服务器在自己身边，有显示器的情况，推荐安装带有物理模拟的habitat-sim
      conda install habitat-sim=0.2.5 withbullet -c conda-forge -c aihabitat
      conda install habitat-sim withbullet -c conda-forge -c aihabitat
    3.考虑到租用服务器的可能性较高，因此，测试仅需要使用example.py即可，在此之前还需要下载一些3d资产，包括一个3d场景和示例对象，关于数据集场景的具体介绍会在第三部分进行详细介绍。（命令中的path/to/可以直接删除变成data/，或者自己更换路径）
      3.1 下载 3D 测试场景（解决Q1和Q2后第2条命令可行）
        python -m habitat_sim.utils.datasets_download --uids habitat_test_scenes --data-path /path/to/data/
        python -m habitat_sim.utils.datasets_download --uids habitat_test_scenes --data-path ~/habitat_data
        这里遇到点问题：
        Q1：更换路径：先创建habita_data目录，再更换路径
        (habitat) dj@DESKTOP-BKHQM7M:~$ mkdir -p ~/habitat_data
        (habitat) dj@DESKTOP-BKHQM7M:~$ python -m habitat_sim.utils.datasets_download --uids habitat_test_scenes --data-path ~/habitat_data
        Q2:Q1解决后还是不行，下载了git-lf后解决
         sudo apt update
         sudo apt install git-lfs
         git lfs install
         rm -rf ~/habitat_data/versioned_data/habitat_test_scenes   //删除之前下载失误的冗余文件
      3.2 下载示例对象
         python -m habitat_sim.utils.datasets_download --uids habitat_example_objects --data-path /path/to/data/
         python -m habitat_sim.utils.datasets_download --uids habitat_example_objects --data-path ~/habitat_data
        如果有显示器的，可以运行以下代码进行测试
         habitat-viewer ~/habitat_data/scene_datasets/habitat-test-scenes/skokloster-castle.glb
