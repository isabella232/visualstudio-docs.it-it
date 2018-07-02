---
title: Funzione CvCreateMarkerSeriesWithCodePageA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63fe3de8c4322e378f110813ac93fa523f3453ba
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750376"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Funzione CvCreateMarkerSeriesWithCodePageA
Crea una serie di marcatori per un provider e una tabella codici specificati. Questa funzione può essere usata per specificare la tabella codici in modo esplicito per il testo scritto da funzioni ANSI dell'API dei marcatori. L'impostazione della tabella codici può risultare utile nel caso in cui la traccia venga acquisita e quindi analizzata in computer diversi con impostazioni locali/linguaggi diversi. Per impostazione predefinita viene usata la tabella codici restituita dalla funzione GetACP().  
  
## <a name="syntax"></a>Sintassi  
  
```C  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProvider`  
 Oggetto provider preinizializzato tramite CvInitProvider. Non può essere NULL.  
  
 `pSeriesName`  
 Nome della serie di marcatori. Non può essere NULL, ma le stringhe vuote sono consentite.  
  
 `nTextCodePage`  
 Tabella codici valida.  
  
 `ppMarkerSeries`  
 Indirizzo di una variabile di output in cui viene memorizzato il contesto della serie di marcatori. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando la serie di marcatori viene creata correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *cvmarkers.h*  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)