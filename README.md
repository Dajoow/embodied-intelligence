# embodied-intelligence
Learn the open-source courses of DataWhale
  Habitat-lab环境搭建
  1.#（如果已经创建了虚拟环境就跳过这步）
      conda create -n habitat python=3.9 cmake=3.14.0  
      conda activate habitat
  2. 在下载habitat-lab的时候注意需要与安装的habitat-sim版本一致，例如本教程使用的habitat-sim版本是0.2.5，则需要下载0.2.5版本的habitat-lab，复现其他论文的时候也要注意habitat-sim和habitat-lab版本一致。
      git clone --branch v0.2.5 https://github.com/facebookresearch/habitat-lab.git
      cd habitat-lab
      pip install -e habitat-lab
  3. 同时安装habitat-baselines
      pip install -e habitat-baselines
  4. 下载3D场景数据和点导航数据
      python -m habitat_sim.utils.datasets_download --uids habitat_test_scenes --data-path data/
      python -m habitat_sim.utils.datasets_download --uids habitat_test_pointnav_dataset --data-path data/
