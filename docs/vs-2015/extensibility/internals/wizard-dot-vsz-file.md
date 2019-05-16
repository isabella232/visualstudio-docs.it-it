---
title: Procedura guidata (. File vsz) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab1adde4c7018f136f47769e16a8ce2fedf72c93
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687669"
---
# <a name="wizard-vsz-file"></a>File (con estensione vsz) della procedura guidata
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'ambiente di sviluppo integrato (IDE) usa i file con estensione vsz per avviare le procedure guidate. Questi file VSZ contengono informazioni utilizzate per determinare quale procedura guidata per chiamare l'IDE e quali informazioni per passare alla procedura guidata.  
  
 Un file VSZ è una versione di un file di testo in formato con estensione ini che non dispone di sezioni. Le informazioni note all'IDE viene archiviate all'inizio del file. Ciò fornisce un collegamento tra la procedura guidata che chiama l'IDE e i parametri nel file VSZ da passare all'IDE. Il resto del file contiene i parametri che sono specifici per la procedura guidata e che devono essere raccolti dall'IDE e passati alla procedura guidata specifica.  
  
 Nell'esempio seguente viene illustrato il contenuto di un file con estensione vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Di seguito sono le parti nel file vsz.  
  
|Parte|Descrizione|  
|----------|-----------------|  
|VSWizard|Il primo parametro nel file è il numero di versione del formato di file del modello. Questo numero di versione deve essere 6.0, 7.0, 7.1 o 8.0. Altri numeri non possono essere avviati e causano un errore di formato non valido.|  
|Wizard|Questo campo contiene il ProgID OLE della procedura guidata o in alternativa una rappresentazione di stringa GUID del CLSID della procedura guidata che viene cocreata dall'IDE.|  
|Param|Queste parti sono facoltative. È possibile aggiungere fino a necessari.|  
  
 I parametri di abilitare il file con estensione vsz passare i parametri personalizzati aggiuntivi per la procedura guidata. Ogni valore viene passato come un elemento di stringa in una matrice di variant per la procedura guidata. Per altre informazioni, vedere [parametri personalizzati](../../extensibility/internals/custom-parameters.md). Per informazioni su come usare un file con estensione vsz nello sviluppo di procedure guidate personalizzate, vedere [. File VSZ (controllo progetto)](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 Per aggiungere un ID impostazioni locali predefinite per il file con estensione vsz, specificare `FALLBACK_LCID`= xxxx, dove xxxx è l'ID delle impostazioni locali, ad esempio, 1033 per inglese. Quando `FALLBACK_LCID` parametro è definito, la procedura guidata Usa l'ID impostazioni locali di fallback specificato se non viene trovato l'ID corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
