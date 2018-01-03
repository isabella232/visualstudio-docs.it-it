---
title: StartTrackingContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StartTrackingContext
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38a04c735584722ba2cac4f608cf558aae03382a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="starttrackingcontext"></a>StartTrackingContext
Avvia un contesto di verifica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>Parametri  
 [in] `intermediateDirectory`  
 Directory in cui archiviare il log di rilevamento.  
  
 [in] `taskName`  
 Identifica il contesto di verifica. Questo nome viene usato per creare il nome del file di log.  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di rilevamento è stato creato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** FileTracker.h