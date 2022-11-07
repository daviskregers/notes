# Pull script

```
for D in ~/Sites/*/;
do
    echo $D
    cd $D && git pull
done
```