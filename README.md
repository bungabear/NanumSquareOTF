# NanumSquareOTF

폰트 출처 : https://hangeul.naver.com/2017/nanum  
네이버 나눔 스퀘어 OTF 

Flutter Dynamic Font용  


```dart
import 'dart:ui';

import 'package:dynamic_fonts/dynamic_fonts.dart';
import 'package:flutter/material.dart';

class NanumSquareFont extends DynamicFontsFile {

  final DynamicFontsVariant variant;
  final NanumSquareFontType type;
  static final String fontFamily = 'NanumSquare';

  NanumSquareFont(this.variant)
      :
        type = NanumSquareFontTypeEx.getType(variant),
        super(NanumSquareFontTypeEx.getType(variant).hash, NanumSquareFontTypeEx.getType(variant).size);

  /// ThemeData.textTheme 에 적용
  static TextTheme getTextTheme({TextTheme textTheme}){
    return DynamicFonts.getTextTheme(
      NanumSquareFont.fontFamily,
      textTheme,
    );
  }

  /// main super.initState() 위에 선언
  static register(){
    print('$fontFamily register start');
    DynamicFonts.register(
      fontFamily,
      FontWeight.values.map((FontWeight fontWeight){
        return NanumSquareFont(
          DynamicFontsVariant(
            fontWeight: fontWeight,
            fontStyle: FontStyle.normal,
          ),
        );
      }).toList()
          .fold<Map<DynamicFontsVariant, DynamicFontsFile>>(
        {},
            (acc, file) => acc..[file.variant] = file,
      ),
    );
    print('$fontFamily registerd');
  }

  @override
  String get url {
    String url = 'https://github.com/bungabear/NanumSquareOTF/blob/main/NanumSquareOTF_${type.fileFix}.otf?raw=true';
    print('$fontFamily call $url');
    return url;
  }
}

enum NanumSquareFontType {
  Light, Regular, Bold, ExtraBold
}

extension NanumSquareFontTypeEx on NanumSquareFontType{

  // 폰트 타입 분기
  static NanumSquareFontType getType(DynamicFontsVariant variant) {
    NanumSquareFontType type = NanumSquareFontType.Regular;
    switch(variant.fontWeight){
      case FontWeight.w100:
        type = NanumSquareFontType.Light;
        break;
      case FontWeight.w200:
        type = NanumSquareFontType.Light;
        break;
      case FontWeight.w300:
        type = NanumSquareFontType.Light;
        break;
      case FontWeight.w400:
        type = NanumSquareFontType.Regular;
        break;
      case FontWeight.w500:
        type = NanumSquareFontType.Regular;
        break;
      case FontWeight.w600:
        type = NanumSquareFontType.Regular;
        break;
      case FontWeight.w700:
        type = NanumSquareFontType.Bold;
        break;
      case FontWeight.w800:
        type = NanumSquareFontType.Bold;
        break;
      case FontWeight.w900:
        type = NanumSquareFontType.ExtraBold;
        break;
      default:
        print('font type error ${variant.fontWeight}');
    }
    return type;
  }

  String getFileFix(DynamicFontsVariant variant){
    return getType(variant).fileFix;
  }

  /// 파일 해쉬 선언
  String get hash{
    switch(this){
      case NanumSquareFontType.Light:
        return '4f1fc6d5a51f9fadc2572fcd6051b8f1df83056a56bcfa547e2611b1eab52953';
      case NanumSquareFontType.Regular:
        return '7022769b1a01760c619912991268b0a93f406ccc519d27705333d09e6ce54efd';
      case NanumSquareFontType.Bold:
        return '51576163fdbb078780cedab8793c49356379385811c768b76951b730875069f0';
      case NanumSquareFontType.ExtraBold:
        return '49353a363ab6c0c9e47c9c0197d8f14000f2c19d1c4c7a8cdd5d56aaacc05666';
    }
  }

  /// 파일크기 선언
  int get size{
    switch(this){
      case NanumSquareFontType.Light:
        return 310196;
      case NanumSquareFontType.Regular:
        return 310344;
      case NanumSquareFontType.Bold:
        return 309976;
      case NanumSquareFontType.ExtraBold:
        return 318604;
    }
  }

  /// 파일명 선언
  String get fileFix{
    switch(this){
      case NanumSquareFontType.Light:
        return 'acL';
      case NanumSquareFontType.Regular:
        return 'acR';
      case NanumSquareFontType.Bold:
        return 'acB';
      case NanumSquareFontType.ExtraBold:
        return 'acEB';
    }
  }
}
```
