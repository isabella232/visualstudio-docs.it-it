---
title: Elemento KeyBinding | Microsoft Docs
description: L'elemento KeyBinding specifica i tasti di scelta rapida per i comandi. Ai comandi possono essere associate sia associazioni di tasti singole che doppie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: be359809e973d8fbb0e1fe0b964d04bc3e41b5d8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152302"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
L'elemento KeyBinding specifica i tasti di scelta rapida per i comandi.

 Ai comandi possono essere associate sia associazioni di tasti singole che doppie. Un esempio di una singola associazione di tasti **è CTRL** + **S** per il **comando** Salva. Le associazioni a due tasti richiedono due combinazioni di tasti successive per attivare un comando. Un esempio di associazione a due tasti è <strong>CTRL *+</strong> K <strong>,</strong>CTRL <strong>+</strong> K** per impostare un segnalibro.

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
|editor|Obbligatorio. Il GUID dell'editor indica il contesto di modifica per cui sarà attivo questo tasto di scelta rapida. Il valore dell'ambito di associazione globale è "guidVSStd97".|
|key1|Obbligatorio. I valori validi includono tutti i caratteri alfanumerici tipizzabili e i valori esadecimali a due cifre preceduti da 0x [e VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|facoltativo. Qualsiasi combinazione **di CTRL,** **ALT** **e MAIUSC** separati da spazio.|
|key2|facoltativo. I valori validi includono tutti i caratteri alfanumerici tipizzabili e i valori esadecimali a due cifre preceduti da 0x [e VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|facoltativo. Qualsiasi combinazione **di CTRL,** **ALT** **e MAIUSC** separati da spazio.|
|emulatore|facoltativo.|
|Condition|facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Padre||
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
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
