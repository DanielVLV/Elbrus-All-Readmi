# [Содержание](../README.md)

# Создание связи many-to-many
Для связи many-to-many используется промежуточная таблица, которая содержит в себе айдишники из обеих таблиц.

В миграции для промежуточной таблицы нужно прописать рефернсы:  
```js
firstId: {
    type: Sequelize.INTEGER, 
    references: {
        model: {
          tableName: 'firstTable',
        },
        key: 'id'
    }
},
secondId: {
  type: Sequelize.INTEGER,
    references: {
    model: {
      tableName: 'secondTable',
    },
    key: 'id'
  }
},
```
В двух таблицах, которые необходимо связать прописываем в ассоциациях:
```js
// FirstModel
this.belongsToMany(models.SecondModel, {
  through: models.Something,
  foreignKey: 'firstId',
});

//SecondModel
this.belongsToMany(models.FirstModel, {
  through: models.Something,
  foreignKey: 'secondId',
});
```
Саму третью модель мы не меняем

