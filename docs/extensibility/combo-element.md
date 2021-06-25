---
title: Elemento Combo | Microsoft Docs
description: "L'elemento Combo definisce i comandi visualizzati in una casella combinata. Sono disponibili quattro tipi: DropDownCombo, DynamicCombo, IndexCombo e MRUCombo."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 431d68b6e545506f5fc90cc5a98a52dd4f1c33ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904955"
---
# <a name="combo-element"></a>Elemento combinato
Definisce i comandi visualizzati in una casella combinata. Esistono quattro tipi di caselle combinate, come indicato di seguito: DropDownCombo, DynamicCombo, IndexCombo e MRUCombo.

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
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|
|defaultWidth|Obbligatorio. Intero che specifica una larghezza in pixel per la casella combinata.|
|idCommandList|Obbligatorio. ID inviato alla destinazione del comando attivo per recuperare l'elenco di elementi da visualizzare nella casella combinata. L'ID sarà nello stesso ambito GUID del controllo.|
|priority|facoltativo. Valore numerico che specifica la priorità.|
|tipo|facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non specificato, usa Button.<br /><br /> DropDownCombo<br /> Il pacchetto VSPackage è responsabile della compilazione del contenuto di questa casella combinata. L'utente non può digitare alcun elemento nella casella di testo di questo elenco a discesa.<br /><br /> DynamicCombo<br /> Il pacchetto VSPackage è responsabile della compilazione del contenuto di questa casella combinata. L'utente può modificare questa casella combinata e selezionare anche gli elementi in essa presenti.<br /><br /> IndexCombo<br /> Uguale a DynamicCombo, ad eccezione del fatto che genera l'indice dell'elemento anziché il relativo testo.<br /><br /> MRUCombo<br /> Compilato dall'ambiente di sviluppo integrato (IDE) per conto del pacchetto VSPackage.  L'utente può modificare in questa casella combinata. L'IDE memorizza fino alle ultime 16 voci per casella combinata.<br /><br /> Quando l'utente seleziona un elemento nella casella combinata o immette qualcosa di nuovo, l'IDE invia una notifica al pacchetto VSPackage appropriato.|
|Condizione|facoltativo. Vedere [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Padre|facoltativo. Elemento padre del pulsante.|
|Flag di comando|Obbligatorio. Vedere [Elemento flag command](../extensibility/command-flag-element.md). I valori validi di CommandFlag per un controllo Button sono i seguenti.<br /><br /> - Senza distinzione tra maiuscole e minuscole<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Stringhe|Obbligatorio. Vedere [Elemento Strings.](../extensibility/strings-element.md) L'elemento ButtonText figlio deve essere definito.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi sulla barra degli strumenti del pacchetto VSPackage.|

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
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
