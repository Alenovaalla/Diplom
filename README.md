
#### Подготовка к запуску автотестов: ####
1. Запустить в Docker контейнеры СУБД MySQl, PostgerSQL и контейнер на Node.js
1. Запустить тестируемое приложение

#### Тестирование на СУБД MySQl: ####
1. Запустить контейнеры СУБД MySQl, PostgerSQL и Node.js командой в терминале:  
`docker-compose up`
1. В новом терминале запустить SUT, работающей на СУБД MySQl командой:  
`java -Dspring.datasource.url=jdbc:mysql://192.168.99.100:3306/app -jar artifacts/aqa-shop.jar` 
1. В новом терминале запустить авто-тесты командой:  
`gradlew clean test -Dspring.datasource.url=jdbc:mysql://192.168.99.100:3306/app`
1. Посмотреть отчет о тестировании Allure командой:  
`gradlew allureReport`
1. Закрыть все контейнеры командой:  
`docker-compose down`

#### Тестирование на СУБД PostgerSQL: ####
1. Запустить контейнеры MySQl, PostgerSQL и Node.js командой в терминале:  
 `docker-compose up`
1. В новом терминале запустить SUT, работающей на СУБД PostgerSQL командой:  
`java -Dspring.datasource.url=jdbc:postgresql://192.168.99.100:5432/app -jar artifacts/aqa-shop.jar `
1. В новом терминале запустить авто-тесты командой:  
`gradlew clean test -Dspring.datasource.url=jdbc:postgresql://192.168.99.100:5432/app`
1. Посмотреть отчет о тестировании Allure командой:  
`gradlew allureReport`
1. Закрыть все контейнеры командой:  
`docker-compose down`
