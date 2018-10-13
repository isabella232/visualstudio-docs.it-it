---
title: Elemento KeyBinding | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 808897b632353e47185cdbd5606d6f2eed1361b0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231818"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento KeyBinding specifica tasti di scelta rapida per i comandi.  
  
 I comandi possono avere una o due tasti di scelta rapida associati. È di un esempio di un unico tasto di scelta rapida CTRL + S per il **salvare** comando. Tasti di scelta doppia richiedono due combinazioni di tasti successive per attivare un comando. Un esempio di un tasto di scelta rapida doppia è CTRL + K, CTRL + K per impostare un segnalibro.  
  
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
|ID|Obbligatorio.|  
|editor|Obbligatorio. Il GUID dell'editor indica il contesto di modifica per il quale sarà attiva questo tasto di scelta rapida. Il valore dell'ambito dell'associazione globale è "guidVSStd97".|  
|key1|Obbligatorio. I valori validi includono tutti i caratteri alfanumerici possibile digitare e inoltre valori esadecimali a due cifre preceduti da 0 x e VK_constants.|  
|MOD1|Facoltativo. Qualsiasi combinazione di CTRL, ALT e MAIUSC separati da spazio.|  
|key2|Facoltativo. I valori validi includono tutti i caratteri alfanumerici possibile digitare e inoltre valori esadecimali a due cifre preceduti da 0 x e VK_constants.|  
|MOD2|Facoltativo. Qualsiasi combinazione di CTRL, ALT e MAIUSC separati da spazio.|  
|Emulatore|Facoltativo.|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre||  
|Annotazione||  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Raggruppa gli elementi di tasto di scelta rapida e altri raggruppamenti di tasti di scelta rapida.|  
  
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
 [Elemento KeyBindings](../extensibility/keybindings-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

