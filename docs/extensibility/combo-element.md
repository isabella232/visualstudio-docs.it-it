---
title: 'Elemento Combo : Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739815"
---
# <a name="combo-element"></a>Elemento combinato
Definisce i comandi visualizzati in una casella combinata. Esistono quattro tipi di caselle combinate, come segue: DropDownCombo, DynamicCombo, IndexCombo e MRUCombo.

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
|guid|Obbligatorio. GUID dell'identificatore di comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore di comando GUID/ID.|
|DefaultWidth (Larghezza predefinita)|Obbligatorio. Intero che specifica una larghezza in pixel per la casella combinata.|
|idCommandList (elenco di comando)|Obbligatorio. ID inviato alla destinazione del comando attivo per recuperare l'elenco di elementi da visualizzare nella casella combinata. L'ID sarà nello stesso ambito GUID del controllo.|
|priority|Facoltativa. Valore numerico che specifica la priorità.|
|type|Facoltativa. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non specificato, utilizza Button.<br /><br /> Proprietà DropDownCombo<br /> Il pacchetto VSPackage è responsabile della compilazione del contenuto per questa casella combinata. L'utente non può digitare nulla nella casella di testo di questo elenco a discesa.<br /><br /> DynamicCombo<br /> Il pacchetto VSPackage è responsabile per la compilazione del contenuto di questa casella combinata. L'utente può modificare questa combinazione e anche selezionare gli elementi in essa contenuti.<br /><br /> IndiceCombo<br /> Uguale a DynamicCombo, ad eccezione del fatto che genera l'indice dell'elemento anziché il relativo testo.<br /><br /> MRUCombo<br /> Compilato dall'ambiente di sviluppo integrato (IDE) per conto del pacchetto VSPackage.  L'utente può modificare in questa casella combinata. L'IDE memorizza fino alle ultime 16 voci per casella combinata.<br /><br /> Quando l'utente seleziona un elemento nella casella combinata o immette un nuovo elemento, l'IDE notifica il pacchetto VSPackage appropriato.|
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Parent|Facoltativa. Elemento padre del pulsante.|
|CommandFlag (Flag di comando)|Obbligatorio. Consultate [Elemento flag di comando](../extensibility/command-flag-element.md). I valori CommandFlag validi per un Button sono i seguenti.<br /><br /> - CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Stringhe|Obbligatorio. Consultate [l'elemento Strings](../extensibility/strings-element.md). È necessario definire l'elemento figlio ButtonText.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi sulla barra degli strumenti VSPackage.|

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
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
