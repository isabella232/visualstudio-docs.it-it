---
title: Funzione SccQueryInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f951e7ef29fbba7225997276b31bd9f32731efc8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108438"
---
# <a name="sccqueryinfo-function"></a>Funzione SccQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione Ottiene informazioni sullo stato per un set di file selezionati nel controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 nFiles  
 [in] Numero di file specificato per il `lpFileNames` matrice e la lunghezza del `lpStatus` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di file sottoposti a query.  
  
 lpStatus  
 [in, out] Matrice in cui il controllo del codice sorgente del plug-in restituisce i flag di stato per ogni file. Per altre informazioni, vedere [File di codice di stato](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Query completata.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente causato da problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_PROJNOTOPEN|Il progetto non è aperto nel controllo del codice sorgente.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Se `lpFileName` è una stringa vuota, non sono attualmente disponibili informazioni di stato da aggiornare. In caso contrario, è il nome e percorso completo del file per cui le informazioni sullo stato sia stato modificato.  
  
 Alla matrice restituita può essere una maschera di bit di `SCC_STATUS_xxxx` bits. Per altre informazioni, vedere [File di codice di stato](../extensibility/file-status-code-enumerator.md). Un sistema di controllo di origine potrebbe non supportare tutti i tipi di bit. Ad esempio, se `SCC_STATUS_OUTOFDATE` non è disponibile, ma non viene impostato il bit.  
  
 Quando si usa questa funzione per estrarre i file, tenere presente quanto segue `MSSCCI` i requisiti di stato:  
  
- `SCC_STATUS_OUTBYUSER` viene impostato quando l'utente corrente ha estratto il file.  
  
- `SCC_STATUS_CHECKEDOUT` non può essere impostata a meno che non `SCC_STATUS_OUTBYUSER` è impostata.  
  
- `SCC_STATUS_CHECKEDOUT` viene impostato solo quando il file viene estratto nella directory di lavoro designato.  
  
- Se il file è stato estratto dall'utente corrente in una directory diversa dalla directory di lavoro `SCC_STATUS_OUTBYUSER` è impostata ma `SCC_STATUS_CHECKEDOUT` non.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)
