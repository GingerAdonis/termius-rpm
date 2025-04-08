# termius-rpm

Unofficial port of [Termius](https://termius.com/) for [Fedora](https://fedoraproject.org/).

## Building instructions

1. Clone the repo, and cd into the directory

```bash
git clone https://github.com/Wallvon/termius-rpm
cd termius-rpm
```

2. Install the build dependencies

```bash
sudo dnf install -y rpmdevtools rpm-build rpm-devel rpmlint bsdtar dnf-plugins-core
```

3. Set up development build tree, download Termius deb to it and build the package.

```bash
rpmdev-setuptree
spectool -g -R termius-app.spec
dnf builddep -y termius-app.spec
rpmbuild --target x86_64 -bb termius-app.spec
```

4. Install the package. It may be called something else depending on your distribution.

```bash
sudo rpm -i ~/rpmbuild/RPMS/x86_64/termius-app-8.6.0-1.fc39.x86_64.rpm
```
