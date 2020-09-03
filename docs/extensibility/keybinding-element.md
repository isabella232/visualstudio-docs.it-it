---
title: Elemento di associazione tasto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703149"
---
# <a name="keybinding-element"></a>Elemento di associazione
L'elemento di associazione di tasti specifica i tasti di scelta rapida per i comandi.

 Ai comandi possono essere associate entrambe le associazioni a chiave singola e doppia. Un esempio di singola chiave di associazione è **CTRL** + **S** per il comando **Save** . Le combinazioni di tasti doppie richiedono due combinazioni di tasti successive per attivare un comando. Un esempio di un doppio tasto di scelta rapida è <strong>CTRL *+</strong> k<strong>,</strong>CTRL <strong>+</strong> k** per impostare un segnalibro.

## <a name="syntax"></a>Sintassi

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio.|
|id|Obbligatorio.|
|editor|Obbligatorio. Il GUID dell'editor indica il contesto di modifica per il quale il tasto di scelta rapida sarà attivo. Il valore dell'ambito di binding globale è "guidVSStd97".|
|key1|Obbligatorio. I valori validi includono tutti i caratteri alfanumerici tipizzabili e anche i valori esadecimali a due cifre preceduti da 0x e [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|Mod1|facoltativo. Qualsiasi combinazione di **CTRL**, **ALT**e **MAIUSC** separati da uno spazio.|
|key2|facoltativo. I valori validi includono tutti i caratteri alfanumerici tipizzabili e anche i valori esadecimali a due cifre preceduti da 0x e [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|MOD2|facoltativo. Qualsiasi combinazione di **CTRL**, **ALT**e **MAIUSC** separati da uno spazio.|
|emulatore|facoltativo.|
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Parent||
|Annotazione||

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Portatasti](../extensibility/keybindings-element.md)|Raggruppa gli elementi di associazione di tasti e altri raggruppamenti di tasti di scelta.|

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
- [Elemento Portatasti](../extensibility/keybindings-element.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
