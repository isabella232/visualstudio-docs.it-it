---
title: IDebugExpressionContext::ParseLanguageText | Microsoft Docs
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
ms.openlocfilehash: 50f9f398b9193c776f8e2a823b78ce7b8da438b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153474"
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
 [in] Fornisce il testo dell'espressione o una o più istruzioni.  
  
 `nRadix`  
 [in] Radice da utilizzare.  
  
 `pstrDelimiter`  
 [in] Il delimitatore di fine-di--blocco di script. Quando si `pstrCode` viene analizzata da un flusso di testo, l'host utilizza un delimitatore, in genere, ad esempio due virgolette ("), per rilevare la fine del blocco di script. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo il motore di scripting fornire alcuni condizionale pre-elaborazioni primitive (ad esempio, sostituire una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) viene utilizzato il motore scripting queste informazioni dipendono dal motore di script. Impostare questo parametro su `NULL` se l'host non utilizzava un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 [in] Combinazione dei flag di testo debug seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica che il testo è un'espressione anziché un'istruzione. Questo flag può influenzare le modalità in cui il testo viene analizzato per alcune lingue.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se un valore restituito è disponibile, si verrà utilizzato dal chiamante.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Non consentire gli effetti collaterali. Se questo flag è impostato, la valutazione dell'espressione dovrebbe modificare nessuno stato di runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Consente i punti di interruzione durante la valutazione del testo. Se questo flag non è impostato i punti di interruzione vengono ignorati durante la valutazione del testo.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Consente a segnalazioni di errore durante la valutazione del testo. Se questo flag non è impostato quindi gli errori non vengono segnalati all'host durante la valutazione.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica l'espressione deve essere valutata per un contesto di codice piuttosto che in esecuzione l'espressione stessa|  
  
 `ppe`  
 [out] Restituisce l'espressione di debug per il testo specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un'espressione di debug per il testo specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)