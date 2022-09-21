# [stable helm charts](https://medium.com/@mattiaperi/create-a-public-helm-chart-repository-with-github-pages-49b180dbb417)

```bash
CHART=charts.jfrog.io
PROJECT=~/.github.repos/${CHART}
##  cd ~/.github.repos && rm -rf ${PROJECT} && ls -la
mkdir -pv ${PROJECT} && cd ${PROJECT}

export ORG=$(cat ../.org)
export GIT_URL=github.com/${ORG}/${CHART}.git
echo "https://${GIT_URL}"

git clone https://${GIT_URL} . && \
  git config --local core.editor "code --wait" && \
  git config --local user.name "Paul Maxfield" && \
  git config --local user.email ${ORG}@users.noreply.github.com

echo -e "User-Agent: *\nDisallow: /" > robots.txt

helm pull jfrog/xray --version 103.49.0
helm lint xray
```
