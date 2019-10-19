---
title: Enumerazione SOURCE_TEXT_ATTR | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572998"
---
# <a name="source_text_attr-enumeration"></a>Enumerazione SOURCE_TEXT_ATTR
Descrivono gli attributi di un singolo carattere di un testo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Members  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Il carattere fa parte di una parola chiave del linguaggio, ad esempio la parola chiave VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Il carattere fa parte di un blocco di commento.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Il carattere non fa parte del testo di origine del linguaggio compilato. Ad esempio, il codice HTML che circonda un blocco di script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Il carattere fa parte di un operatore di linguaggio. Ad esempio:, l'operatore aritmetico **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Il carattere fa parte di una costante numerica della lingua.  Ad esempio, la costante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Il carattere fa parte di una costante di stringa della lingua. Ad esempio, la stringa "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Il carattere indica l'inizio di un blocco di funzione|  
  
## <a name="remarks"></a>Note  
 In genere, i metodi `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` e `IActiveScriptDebug::GetScriptTextAttributes` restituiscono un attributo di testo per carattere, a meno che non sia:  
  
- Il flag GETATTRTYPE_DEPSCAN è impostato, nel qual caso il metodo può restituire i flag SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP.  
  
- Il flag GETATTRFLAG_THIS è impostato, nel qual caso il metodo può restituire il flag SOURCETEXT_ATTR_THIS,  
  
- Il flag GETATTRFLAG_HUMANTEXT è impostato, nel qual caso il metodo può restituire il flag SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)