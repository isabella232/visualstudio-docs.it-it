---
title: Elemento Commands | Microsoft Docs
description: "L'elemento Commands rappresenta la raccolta di comandi sulla barra degli strumenti di VSPackage e può avere queste sezioni: menu, gruppi, pulsanti, combinazioni e bitmap."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 35cea63308ffaef653904f4c959164bd09b73df0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146095"
---
# <a name="commands-element"></a>Elemento Commands
Rappresenta la raccolta di comandi sulla barra degli strumenti di VSPackage. La raccolta può avere fino a cinque sottosezioni, come indicato di seguito: menu, gruppi, pulsanti, combinazioni e bitmap.

 Ogni elemento figlio della sottosezione, ad esempio , è identificato da un ID di comando univoco che è una coppia DI GUID e \<Menu> identificatore numerico. Il GUID identifica il "set di comandi" e viene usato per raggruppare comandi correlati logicamente. Il pacchetto VSPackage deve definire il proprio set di comandi per evitare conflitti con gli ID di comando definiti da altri VSPackage.

## <a name="syntax"></a>Sintassi

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|Pacchetto|GUID che identifica il pacchetto VSPackage che fornisce i comandi.<br /><br /> Ad esempio, package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un vspackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene voci che definiscono i gruppi di comandi in un VSPackage.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi Button.|
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Raggruppa gli elementi Bitmap.|
|[Elemento Combos](../extensibility/combos-element.md)|Raggruppa gli elementi combo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi forniti da un vspackage all'IDE. Gli elementi possibili sono voci di menu, menu, barre degli strumenti e caselle combinate.|

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come usare un [elemento Commands](../extensibility/commands-element.md).

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
