---
title: Elemento combo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a97163f1f7dc2a1152bc22f4bc3a68ed32b3cfe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334901"
---
# <a name="combo-element"></a>Elemento combo
Definisce i comandi che vengono visualizzati in una casella combinata. Esistono quattro tipi di caselle combinate, come indicato di seguito: DropDownCombo, DynamicCombo, IndexCombo, and MRUCombo.

## <a name="syntax"></a>Sintassi

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|
|defaultWidth|Obbligatorio. Valore intero che specifica una larghezza in pixel per la casella combinata.|
|idCommandList|Obbligatorio. Un ID che viene inviato alla destinazione del comando attiva per recuperare l'elenco di elementi da visualizzare nella casella combinata. L'ID sarà nello stesso ambito GUID del controllo.|
|priority|Facoltativo. Valore numerico che specifica la priorità.|
|tipo|Facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non viene specificato, viene utilizzata sul pulsante.<br /><br /> DropDownCombo<br /> Il pacchetto VSPackage è responsabile della compilazione del contenuto per questa casella combinata. L'utente non è possibile digitare qualsiasi elemento nella casella di testo di questo elenco a discesa.<br /><br /> DynamicCombo<br /> Il pacchetto VSPackage è responsabile della compilazione nel contenuto di questa casella combinata. L'utente può modificare questa casella combinata e anche selezionare gli elementi in esso.<br /><br /> IndexCombo<br /> Lo stesso come DynamicCombo ad eccezione del fatto che genera l'indice dell'elemento anziché il relativo testo.<br /><br /> MRUCombo<br /> Compilato tramite l'ambiente di sviluppo integrato (IDE) per conto di VSPackage.  L'utente può modificare in questa casella combinata. Nell'IDE vengono mantenuti fino alle ultime 16 voci per ogni casella combinata.<br /><br /> Quando l'utente seleziona un elemento nella casella combinata o immette un nuovo valore, l'IDE di notifica a VSPackage appropriato.|
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Padre|Facoltativo. L'elemento padre del pulsante.|
|CommandFlag|Obbligatorio. Visualizzare [elemento commandflag](../extensibility/command-flag-element.md). I valori CommandFlag validi per un pulsante sono come indicato di seguito.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -FilterKeys<br /><br /> - IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|
|Stringhe|Obbligatorio. Visualizzare [elemento Strings](../extensibility/strings-element.md). Elemento ButtonText figlio deve essere definito.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi sulla barra degli strumenti di VSPackage.|

## <a name="example"></a>Esempio

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>Vedere anche
- [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
