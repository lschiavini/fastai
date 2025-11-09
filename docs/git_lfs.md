# GIT LFS

To track large files on git:
```bash
# installing mac
brew install git-lfs 
# installing on linux
apt-get install git-lfs

# install on repo
git lfs install
git lfs track "*.pkl" # tracks the filetype .pkl, which are trained models in our case
git add .gitattributes
git commit -m "update .gitattributes so git lfs will track .pkl files" # just a commit message really
```