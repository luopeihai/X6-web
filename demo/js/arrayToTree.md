
``` 
        /***
         ** data 为数组类型
         **  return Array
         ***/

        function arrayToTree(data) {
          //data 验证数组格式
          if (!data || typeof data !== "object" || !Array.isArray(data)) {
            return [];
          }

          //根数组
          const parentArray = data.filter(item => item.parent == undefined);
          //子数组
          const childArray = data.filter(item => item.parent !== undefined);

          //查询子节点 方法
          this.selectChild = (parentArray, childArray) => {
            //遍历父类
            parentArray.forEach(parentItem => {
              //遍历子类
              childArray.forEach((childItem, index) => {
                //匹配父类
                if (childItem.parent === parentItem.id) {
                  //备份数组
                  const tempArray = JSON.parse(JSON.stringify(childArray));
                  //去除当前子类
                  tempArray.splice(index, 1);
                  //查询当前子节点 下 子类
                  this.selectChild([childItem], tempArray);

                  parentItem.chidren
                    ? parentItem.chidren.push(childItem)
                    : (parentItem.chidren = [childItem]);
                }
              });
            });
          };

          //递归查询子节点
          this.selectChild(parentArray, childArray);

          return parentArray;
        }

```