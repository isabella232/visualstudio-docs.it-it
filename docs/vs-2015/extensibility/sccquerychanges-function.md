---
title: Funzione SccQueryChanges | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8dea3152dcebeff667df99f52f05f2ac39a50aa6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848644"
---
# <a name="sccquerychanges-function"></a>Funzione SccQueryChanges
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione enumera un elenco di file, che fornisce informazioni sulle modifiche ai nomi per ogni file tramite una funzione di callback.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 nFile  
 [in] Numero di file in `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di file per cui ottenere informazioni.  
  
 pfnCallback  
 [in] Funzione di callback da chiamare per ogni nome di file nell'elenco (vedere [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) per informazioni dettagliate).  
  
 pvCallerData  
 [in] Valore che verrà passati invariato per la funzione di callback.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il processo di query completato.|  
|SCC_E_PROJNOTOPEN|Il progetto non è stata aperta nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|  
  
## <a name="remarks"></a>Note  
 Sottoposto a query per le modifiche sono per lo spazio dei nomi: in particolare, la ridenominazione, aggiunta e rimozione di un file.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Codici di errore](../extensibility/error-codes.md)

