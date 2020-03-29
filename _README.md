# Note
docker login -u thaihust -p *****************

export VERSION=$(curl -s https://my.atlassian.com/download/feeds/confluence.rss | grep -Po "(\d{1,2}\.){2,3}\d" | uniq)

docker build --build-arg VERSION=${VERSION} . -t confluence:${VERSION}

docker tag confluence:${VERSION} thaihust/confluence:${VERSION}
docker push thaihust/confluence:${VERSION}
