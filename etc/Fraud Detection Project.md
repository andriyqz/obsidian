Classification metrics:
PR-AUC (через дизбаланс класів у кагл датасеті)
Recall and precision = 5% (precision за умови, щоб до 5% транзакцій можна помилково визначати як фрод)
Cost matrix як бізнес метрика (хибнопозитивна помилка = - лояльність клієнта, хибнонегативна = - втрачена сума транзакції)
Бейзлайн - рандом форест

Базова інфраструктура:
[Transaction Request] -> [FastAPI Middleware] -> [Fetch Features from Redis] -> [LightGBM Inference] -> [Decision: Allow/Block]
