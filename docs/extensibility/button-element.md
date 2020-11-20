---
title: Elemento Button | Microsoft Docs
description: "L'elemento Button definisce un elemento con cui l'utente può interagire. I pulsanti possono essere tipi diversi: Button, MenuButton e SplitDropDown."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8da92f721f0f4333ffb32ac5cb080d87e4fc0543
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974495"
---
# <a name="button-element"></a>Elemento Button
Definisce un elemento con cui l'utente può interagire. I pulsanti possono essere di tipi diversi: Button, MenuButton e SplitDropDown.

## <a name="syntax"></a>Sintassi

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|
|priority|Facoltativo. Valore numerico che specifica la priorità.|
|tipo|Facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non viene specificato, utilizza il pulsante.<br /><br /> Pulsante<br /> Un comando standard visualizzato sulle barre degli strumenti (in genere un pulsante iconico), i menu e i menu di scelta rapida.<br /><br /> MenuButton<br /> Voce di menu che non esegue un comando, ma produce un altro menu.<br /><br /> SplitDropDown<br /> I controlli, ad esempio i pulsanti Annulla e Ripeti sulla barra degli strumenti standard in Microsoft Word.|
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento padre](../extensibility/parent-element.md)|Facoltativo. Elemento padre del pulsante.|
|[Icon (elemento)](../extensibility/icon-element.md)|Facoltativo. Icona associata al pulsante.|
|[Elemento del flag di comando](../extensibility/command-flag-element.md)|Obbligatorio. I valori CommandFlag validi per un pulsante sono i seguenti.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> -DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> -Nocustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -PICT<br /><br /> -Postexec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> -TEXTCHANGES al<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -TextOnly|
|[Elemento Strings](../extensibility/strings-element.md)|Obbligatorio. È necessario definire l' [elemento ButtonText](../extensibility/buttontext-element.md) figlio.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementi del pulsante gruppi.|

## <a name="example"></a>Esempio
 Nell'esempio seguente viene definito un pulsante in un file con *estensione vsct* .

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
