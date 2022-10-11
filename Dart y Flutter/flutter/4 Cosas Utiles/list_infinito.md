# List Infinito

para hacer un list infinito tendremos que basarnos en el siguiente codigo:

```dart
import 'package:componentes_app/theme/app_theme.dart';
import 'package:flutter/material.dart';


import '../widgets/widgets.dart';

class ListViewBuilderScreen extends StatefulWidget {
  const ListViewBuilderScreen({Key? key}) : super(key: key);

  @override
  State<ListViewBuilderScreen> createState() => _ListViewBuilderScreenState();
}

class _ListViewBuilderScreenState extends State<ListViewBuilderScreen> {
  final List<int> imagenes = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  final ScrollController scrollController = ScrollController();
  bool isLoading = false;

  @override
  void initState() {
    super.initState();
    scrollController.addListener(() {
      if ((scrollController.position.pixels + 500) >=
          scrollController.position.maxScrollExtent) {
        fetchData();
      }
    });
  }

  Future fetchData() async {
    if (isLoading) return;
    isLoading = true;
    setState(() {});

    await Future.delayed(const Duration(seconds: 3));
    add5();
    isLoading = false;
    setState(() {});
    if (scrollController.position.pixels + 100 <=
        scrollController.position.maxScrollExtent) return;
    scrollController.animateTo(scrollController.position.pixels + 120,
        duration: const Duration(seconds: 1), curve: Curves.fastOutSlowIn);
  }

  void add5() {
    final lastId = imagenes.last;
    imagenes.addAll([1, 2, 3, 4, 5].map((e) => lastId + e));
    setState(() {});
  }

  Future<void> onRefresh() async{
    await Future.delayed(const Duration(seconds: 2));
    final lastId = imagenes.last;
    imagenes.clear();
    imagenes.add(lastId+1);
    add5();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Scroll Infinito"),
      ),
      body: Stack(
        children: [
          RefreshIndicator(
            color: AppTheme.second,
            onRefresh: onRefresh,
            child: ListView.separated(
              controller: scrollController,
              itemCount: imagenes.length,
              separatorBuilder: (context, index) => const SizedBox(height: 10),
              itemBuilder: (context, index) {
                return Padding(
                  padding: const EdgeInsets.symmetric(horizontal: 15),
                  child: CustomCardType2(
                      imageUrl:
                          "https://picsum.photos/500/300?random=${imagenes[index]}"),
                );
              },
            ),
          ),
          if (isLoading)
            Positioned(
              bottom: 40,
              left: MediaQuery.of(context).size.width * 0.5 - 25,
              child: const LoadingIcon(),
            )
        ],
      ),
    );
  }
}

class LoadingIcon extends StatelessWidget {
  const LoadingIcon({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.all(7),
      height: 50,
      width: 50,
      decoration: BoxDecoration(
          color: Colors.white.withOpacity(0.9), shape: BoxShape.circle),
      child: const CircularProgressIndicator(color: AppTheme.second),
    );
  }
}
```

## Importante

Para que esto funcione tenemos que cambiar algo del codigo core de flutter del archivo **fade_in_image.dart**

esta linea cercana de a la linea 500:

```dart
@override
  Widget build(BuildContext context) {
    if (widget.wasSynchronouslyLoaded || _placeholderOpacityAnimation!.isCompleted) {
      return widget.target;
    }
```

pasa a ser esta:

```dart
@override
  Widget build(BuildContext context) {
    if (widget.wasSynchronouslyLoaded ||  (_placeholderOpacityAnimation?.isCompleted ?? true)) {
      return widget.target;
    }
```

Nos basamos en [aqui](https://chromium.googlesource.com/external/github.com/flutter/flutter/+/HEAD/packages/flutter/lib/src/widgets/fade_in_image.dart) y [aqui](https://www.udemy.com/course/flutter-ios-android-fernando-herrera/learn/lecture/14423988#questions/18257260)