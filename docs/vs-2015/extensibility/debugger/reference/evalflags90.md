---
title: EVALFLAGS90 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ab44d09b969d36699be2e5ce593d96db4d366af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525508"
---
# <a name="evalflags90"></a>EVALFLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [EVALFLAGS90](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/evalflags90).  
  
Enumera i valori validi per i flag che controllano la valutazione dell'espressione. Questa enumerazione estende la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 EVAL90_RETURNVALUE  
 Specifica che il valore restituito, se presente, da valutare.  
  
 EVAL90_NOSIDEEFFECTS  
 Specifica che gli effetti collaterali non saranno consentite.  
  
 EVAL90_ALLOWBPS  
 Specifica l'arresto per i punti di interruzione.  
  
 EVAL90_ALLOWERRORREPORT  
 Specifica che la segnalazione errori per l'host deve essere autorizzato. Utilizzato principalmente per la valutazione dell'espressione in uno script in Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Funzioni di forze deve essere valutata come indirizzi, anziché richiamare la funzione.  
  
 EVAL90_NOFUNCEVAL  
 Impedisce che funzione viene valutata. Si consideri, ad esempio, il `int` token dell'espressione `myExpression(int) + 10`. Questa funzione può essere valutata correttamente come un indirizzo, ma non come un valore.  
  
 EVAL90_NOEVENTS  
 Flag per indicare che gli eventi che si verificano durante la valutazione dell'espressione non devono essere inviati al gestore di sessione di debug (SDM) o all'IDE.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Abilita valutazione delle espressioni in fase di progettazione.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Consente la creazione di variabili implicita.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Valutazione di forze affinché venga eseguito immediatamente. Ciò è utile quando una richiesta, ad esempio una richiesta dell'utente di manutenzione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

