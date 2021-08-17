---
title: Elemento Button | Microsoft Docs
description: "L'elemento Button definisce un elemento con cui l'utente può interagire. I pulsanti possono essere di diversi tipi: Button, MenuButton e SplitDropDown."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9ad9551e15d3d64b899e2c7e70bf80597193973f0cecc04f2145cf0ecdc4d1c6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452641"
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
|priority|facoltativo. Valore numerico che specifica la priorità.|
|tipo|facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non specificato, usa Button.<br /><br /> Button<br /> Comando standard visualizzato sulle barre degli strumenti (in genere come pulsante icona), menu e menu di scelta rapida.<br /><br /> MenuButton<br /> Voce di menu che non esegue un comando, ma produce un altro menu.<br /><br /> SplitDropDown<br /> Controlli, ad esempio i pulsanti Annulla e Ripeti sulla barra degli strumenti standard in Microsoft Word.|
|Condition|facoltativo. Vedere [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento padre](../extensibility/parent-element.md)|facoltativo. Elemento padre del pulsante.|
|[Elemento Icon](../extensibility/icon-element.md)|facoltativo. Icona associata al pulsante.|
|[Elemento flag di comando](../extensibility/command-flag-element.md)|Obbligatorio. I valori validi di CommandFlag per un controllo Button sono i seguenti.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - Modifiche di testo<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Elemento Strings](../extensibility/strings-element.md)|Obbligatorio. [L'elemento ButtonText figlio](../extensibility/buttontext-element.md) deve essere definito.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi Button.|

## <a name="example"></a>Esempio
 L'esempio seguente definisce un pulsante in un file *con estensione vsct.*

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

## <a name="see-also"></a>Vedi anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
