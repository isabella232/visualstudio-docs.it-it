---
title: IDebugExpressionContext::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573161"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Crea un'espressione di debug per il testo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 in Fornisce il testo dell'espressione o delle istruzioni.  
  
 `nRadix`  
 in Radice da usare.  
  
 `pstrDelimiter`  
 in Delimitatore di blocco di fine dello script. Quando `pstrCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole (''), per rilevare la fine del blocco di script. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo al motore di scripting di fornire una pre-elaborazione condizionale (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole da utilizzare come delimitatore). Il modo in cui (e se) il motore di scripting utilizza queste informazioni dipende dal motore di scripting. Impostare questo parametro su `NULL` se l'host non ha usato un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 in Combinazione dei flag di testo di debug seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica che il testo è un'espressione anziché un'istruzione. Questo flag può influire sul modo in cui il testo viene analizzato da alcune lingue.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se è disponibile un valore restituito, esso verrà usato dal chiamante.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Non consentire effetti collaterali. Se questo flag è impostato, la valutazione dell'espressione non deve modificare lo stato di Runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Consente i punti di interruzione durante la valutazione del testo. Se questo flag non è impostato, i punti di interruzione verranno ignorati durante la valutazione del testo.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Consente la segnalazione di errori durante la valutazione del testo. Se questo flag non è impostato, gli errori non vengono segnalati all'host durante la valutazione.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica che l'espressione deve essere valutata in un contesto di codice anziché eseguire l'espressione stessa|  
  
 `ppe`  
 out Restituisce l'espressione di debug per il testo specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un'espressione di debug per il testo specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)