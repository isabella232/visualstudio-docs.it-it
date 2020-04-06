---
title: Elemento Button . Documenti Microsoft
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
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739933"
---
# <a name="button-element"></a>Elemento Button
Definisce un elemento con cui l'utente può interagire. I pulsanti possono essere di diversi tipi: Button, MenuButton e SplitDropDown.

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
|guid|Obbligatorio. GUID dell'identificatore di comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore di comando GUID/ID.|
|priority|Facoltativa. Valore numerico che specifica la priorità.|
|type|Facoltativa. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non specificato, utilizza Button.<br /><br /> Pulsante<br /> Comando standard visualizzato sulle barre degli strumenti (in genere come pulsante iconico), nei menu e nei menu di scelta rapida.<br /><br /> MenuButton<br /> Voce di menu che non esegue un comando, ma produce un altro menu.<br /><br /> SplitDropDown (SplitDropDown)<br /> Controlli, ad esempio i pulsanti Annulla e Ripeti sulla barra degli strumenti standard di Microsoft Word.|
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento padre](../extensibility/parent-element.md)|Facoltativa. Elemento padre del pulsante.|
|[Elemento icona](../extensibility/icon-element.md)|Facoltativa. Icona associata al pulsante.|
|[Elemento del flag di comando](../extensibility/command-flag-element.md)|Obbligatorio. I valori CommandFlag validi per un Button sono i seguenti.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache (Informazioni in base a<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Elemento Strings](../extensibility/strings-element.md)|Obbligatorio. È necessario definire [l'elemento figlio ButtonText.](../extensibility/buttontext-element.md)|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi Button.|

## <a name="example"></a>Esempio
 Nell'esempio seguente viene definito un pulsante in un file *con estensione vsct.*

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
