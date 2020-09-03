---
title: Elemento di associazione tasto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180324"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento di associazione di tasti specifica i tasti di scelta rapida per i comandi.  
  
 Ai comandi possono essere associate entrambe le associazioni a chiave singola e doppia. Un esempio di singola chiave di associazione è CTRL + S per il comando **Save** . Le combinazioni di tasti doppie richiedono due combinazioni di tasti successive per attivare un comando. Un esempio di un tasto di scelta rapida doppio è CTRL + K, CTRL + K per impostare un segnalibro.  
  
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
|editor|Obbligatorio. Il GUID dell'editor indica il contesto di modifica per il quale il tasto di scelta rapida sarà attivo. Il valore dell'ambito di binding globale è "guidVSStd97".|  
|key1|Obbligatorio. I valori validi includono tutti i caratteri alfanumerici tipizzabili e anche i valori esadecimali a due cifre preceduti da 0x e VK_constants.|  
|Mod1|facoltativo. Qualsiasi combinazione di CTRL, ALT e MAIUSC separati da uno spazio.|  
|key2|facoltativo. I valori validi includono tutti i caratteri alfanumerici tipizzabili e anche i valori esadecimali a due cifre preceduti da 0x e VK_constants.|  
|MOD2|facoltativo. Qualsiasi combinazione di CTRL, ALT e MAIUSC separati da uno spazio.|  
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
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Raggruppa gli elementi di associazione di tasti e altri raggruppamenti di tasti di scelta.|  
  
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
 [Elemento Portatasti](../extensibility/keybindings-element.md)   
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
