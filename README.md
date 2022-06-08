## Sequlize

#### Insert Multiple Column
```nodejs
await User.create({
  firstName: "Nathan"
});
```
#
#### Get All Column
```nodejs
 const users = await User.findAll();
```
#
#### Get Specific Column 
```nodejs
// This is a tiresome way of getting the number of hats (along with every column)
Model.findAll({
  attributes: [
    'id', 'foo', 'bar', 'baz', 'qux', 'hats',
  ] // We had to list all attributes...
});
```
#
#### Get Specific Rows
```nodejs
Post.findAll({
  where: {
    authorId: 2
  }
});
// SELECT * FROM post WHERE authorId = 2;

```
#
#### GET SORTED COLUMN
```nodejs
Company.findAll({
        where: {
            id: [46128, 2865, 49569,  1488,   45600,   61991,  1418,  61919,   53326,   61680]
        }, 
        // Add order conditions here....
        order: [
            ['id', 'DESC'],
            ['name', 'ASC'],
        ],
        attributes: ['id', 'logo_version', 'logo_content_type', 'name', 'updated_at']
    });
```
#
#### GET JOINT
```nodejs
UserAccess.belongsTo(UserMaster,{foreignKey: 'userId'});
UserMaster.hasMany(UserAccess,{foreignKey : 'userId'});
var userData = await UserMaster.findAll({include: [UserAccess]});
```

