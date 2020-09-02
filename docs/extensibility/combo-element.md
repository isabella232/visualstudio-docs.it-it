---
title: Elemento combinato | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739815"
---
# <a name="combo-element"></a>Elemento combinato
Definisce i comandi che vengono visualizzati in una casella combinata. Sono disponibili quattro tipi di caselle combinate, come indicato di seguito: DropDownCombo, DynamicCombo, IndexCombo e MRUCombo.

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

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|
|defaultWidth|Obbligatorio. Intero che specifica la larghezza in pixel della casella combinata.|
|idCommandList|Obbligatorio. ID inviato alla destinazione del comando attiva per recuperare l'elenco di elementi da visualizzare nella casella combinata. L'ID si troverà nello stesso ambito del GUID del controllo.|
|priority|facoltativo. Valore numerico che specifica la priorità.|
|type|facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non viene specificato, utilizza il pulsante.<br /><br /> DropDownCombo<br /> Il pacchetto VSPackage è responsabile del riempimento del contenuto di questa casella combinata. L'utente non può digitare alcun elemento nella casella di testo dell'elenco a discesa.<br /><br /> DynamicCombo<br /> Il pacchetto VSPackage è responsabile del riempimento del contenuto di questa casella combinata. L'utente può modificare questa casella combinata e selezionare anche gli elementi in esso contenuti.<br /><br /> IndexCombo<br /> Uguale a DynamicCombo, ad eccezione del fatto che genera l'indice dell'elemento anziché il testo.<br /><br /> MRUCombo<br /> Compilato dal Integrated Development Environment (IDE) per conto del pacchetto VSPackage.  L'utente può modificare in questa casella combinata. L'IDE memorizza le ultime 16 voci per casella combinata.<br /><br /> Quando l'utente seleziona un elemento nella casella combinata o immette un nuovo elemento, l'IDE invia una notifica al pacchetto VSPackage appropriato.|
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Parent|facoltativo. Elemento padre del pulsante.|
|CommandFlag|Obbligatorio. Vedere [elemento del flag di comando](../extensibility/command-flag-element.md). I valori CommandFlag validi per un pulsante sono i seguenti.<br /><br /> -CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> -Filtro tasti<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> -Nocustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Stringhe|Obbligatorio. Vedere [elemento Strings](../extensibility/strings-element.md). È necessario definire l'elemento ButtonText figlio.|
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
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
