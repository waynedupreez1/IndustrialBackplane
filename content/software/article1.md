Title: My First Article
Date: 2014-05-01 10:35
Category: Software
Author: Wayne du Preez
icon: automobile

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin dignissim lorem consequat, malesuada dolor quis, gravida est. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Maecenas vitae pulvinar nisl. Vestibulum blandit risus enim, in pharetra felis rutrum sit amet.


Let's test some syntax highlighting:
```python
@hosts(production)
def publish():
    local('pelican -s publishconf.py')
    project.rsync_project(
        remote_dir=dest_path,
        exclude=".DS_Store",
        local_dir=DEPLOY_PATH.rstrip('/') + '/',
        delete=True
    )
```