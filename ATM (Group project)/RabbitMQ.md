# RabbitMQ Stockbrood

## Strategy upload

When trader uploads a strategy to the platform it will send a request to StratService which will save it in its own MongoDB. Meanwhile, the TestManager also needs the uploaded strategy for running tests. So, when uploading to StratService it will send a RabbitMQ message to TestManager which will only save the necesary information to run test in MongoDB.   

![StrategyUpload](https://github.com/Adv-Software-DeKeet/.github/blob/main/ATM%20(Group%20project)/images/StrategyUpload.png)