void main() {
  final countOfCities = 5;
  var minValue = double.infinity;
  dynamic tour = null;
  List<List<int>> result = [List.from(citiesMap)];
  // Here its 0..5
  for (int i = 0; i < citiesMap.length - 1; i++) {
    var res;
    for (int j = 0; j < citiesMap.skip(i + 1).length; j++) {
      List<int> tempMap = List.from(citiesMap);
      final tempi = tempMap[i];
      final tempj = tempMap[i + j + 1];
      tempMap[i] = tempj;
      tempMap[i + j + 1] = tempi;
      result.add(tempMap);
      // Добавим в начало и конец пути первый (нулевой) город
      tempMap.add(0);
      tempMap.insert(0, 0);
      // Получим расстояния для каждого перехода и суммируем их
      res = tempMap;
      int summary = 0;
      for (int a = 0; a < res.length - 1; a++) {
        final routeMass = map[res[a]][res[a + 1]]!;
        summary += map[res[a]][res[a + 1]]!;
      }
      if (summary < minValue) {
        minValue = summary.floorToDouble();
        tour = tempMap;
      }
    }
  }

  print('Yahoo! With minimal result $minValue the best way is $tour !!!');
}

final map = [
  [null, 1, 2, 7, 5],
  [1, null, 4, 4, 3],
  [2, 4, null, 1, 2],
  [7, 4, 1, null, 3],
  [5, 3, 2, 3, null]
];

final citiesMap = [1, 2, 3, 4];

int factorial(int number) {
  var factorial = 1;

  for (var i = number; i >= 1; i--) {
    factorial *= i;
  }
  return (factorial);
}
