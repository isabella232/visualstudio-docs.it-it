---
title: Elemento Commands . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739682"
---
# <a name="commands-element"></a>Elemento Commands
Rappresenta la raccolta di comandi sulla barra degli strumenti VSPackage. La raccolta può avere fino a cinque sottosezioni, come indicato di seguito: menu, gruppi, pulsanti, combinazioni e bitmap.

 Ogni elemento figlio della sottosezione, ad esempio \<> Menu, è identificato da un ID di comando univoco che è una coppia GUID e identificatore numerico. Il GUID identifica il "set di comandi" e viene utilizzato per raggruppare i comandi correlati logicamente. Il pacchetto VSPackage deve definire il proprio set di comandi per evitare conflitti con gli ID di comando definiti da altri pacchetti VSPackage.The VSPackage should define its own command set to avoid collisions with command IDs that are defined by other VSPackages.

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
|Pacchetto|GUID che identifica il pacchetto VSPackage che fornisce i comandi.<br /><br /> Ad esempio, package:"guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un pacchetto VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene voci che definiscono i gruppi di comandi in un pacchetto VSPackage.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi Button.|
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Raggruppa gli elementi Bitmap.|
|[Elemento Combos](../extensibility/combos-element.md)|Raggruppa gli elementi combinati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un VSPackage fornisce all'IDE. Gli elementi possibili sono voci di menu, menu, barre degli strumenti e caselle combinate.|

## <a name="example"></a>Esempio
 Nell'esempio riportato di seguito viene illustrato come utilizzare un [elemento Commands](../extensibility/commands-element.md).

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

## <a name="see-also"></a>Vedere anche
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
