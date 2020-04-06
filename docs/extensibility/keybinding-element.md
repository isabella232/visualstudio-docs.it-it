---
title: Elemento KeyBinding . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703149"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
L'elemento KeyBinding specifica i tasti di scelta rapida per i comandi.

 Ai comandi possono essere associate associazioni di tasti sia singole che doppie. Un esempio di un singolo tasto di scelta rapida è Ctrl S per il comando **Salva.An** example of a single key binding is **Ctrl**+**S** for the Save command. Le associazioni di tasti doppie richiedono due combinazioni di tasti successive per attivare un comando. Un esempio di un doppio legame di tasti è <strong>Ctrl*+</strong>K<strong>,</strong>Ctrl<strong>+</strong>K*- per impostare un segnalibro.

## <a name="syntax"></a>Sintassi

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio.|
|id|Obbligatorio.|
|editor|Obbligatorio. Il GUID dell'editor indica il contesto di modifica per il quale questa scelta rapida da tastiera sarà attiva. Il valore dell'ambito di associazione globale è "guidVSStd97".|
|key1|Obbligatorio. I valori validi includono tutti gli alfanumerici tipoti e anche i valori esadecimali a due cifre preceduti da 0x e [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1 (informazioni in stato indue|Facoltativa. Qualsiasi combinazione di **Ctrl**, **Alt**e **Maiusc** separati da spazio.|
|key2|Facoltativa. I valori validi includono tutti gli alfanumerici tipoti e anche i valori esadecimali a due cifre preceduti da 0x e [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Facoltativa. Qualsiasi combinazione di **Ctrl**, **Alt**e **Maiusc** separati da spazio.|
|emulatore|Facoltativa.|
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Parent||
|Annotazione||

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Raggruppa gli elementi KeyBinding e altri raggruppamenti KeyBindings.|

## <a name="example"></a>Esempio

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Vedere anche
- [Elemento KeyBindings](../extensibility/keybindings-element.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
