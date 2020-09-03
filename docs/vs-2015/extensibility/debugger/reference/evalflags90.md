---
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a95f25f9e970beb31544722b1beeb05b2d480b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156042"
---
# <a name="evalflags90"></a>EVALFLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enumera i valori validi per i flag che controllano la valutazione dell'espressione. Questa enumerazione estende l'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) .  
  
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
 Specifica che il valore restituito, se presente, deve essere valutato.  
  
 EVAL90_NOSIDEEFFECTS  
 Specifica che gli effetti collaterali non sono consentiti.  
  
 EVAL90_ALLOWBPS  
 Specifica l'arresto in corrispondenza di punti di interruzione.  
  
 EVAL90_ALLOWERRORREPORT  
 Specifica che la segnalazione degli errori all'host deve essere consentita. Utilizzato principalmente per la valutazione di espressioni nello script in Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Impone la valutazione delle funzioni come indirizzi, anziché richiamare la funzione.  
  
 EVAL90_NOFUNCEVAL  
 Impedisce la valutazione della funzione. Si consideri, ad esempio, il `int` token nell'espressione `myExpression(int) + 10` . Questa funzione può essere valutata correttamente come un indirizzo, ma non come valore.  
  
 EVAL90_NOEVENTS  
 Flag che indica che gli eventi che si verificano durante la valutazione dell'espressione non devono essere inviati a gestione debug sessione (SDM) o all'IDE.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Abilita la valutazione delle espressioni in fase di progettazione.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Consente la creazione di variabili implicite.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Forza la valutazione a essere eseguita immediatamente. Questa operazione è utile per la manutenzione di una richiesta, ad esempio una richiesta dell'utente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg90. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
