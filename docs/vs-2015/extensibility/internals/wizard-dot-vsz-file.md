---
title: Procedura guidata (. File VSZ) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687669"
---
# <a name="wizard-vsz-file"></a>File (con estensione vsz) della procedura guidata
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il Integrated Development Environment (IDE) utilizza i file con estensione vsz per avviare le procedure guidate. Questi file con estensione vsz contengono informazioni utilizzate dall'IDE per determinare quale procedura guidata chiamare e quali informazioni passare alla procedura guidata.  
  
 Un file con estensione vsz è una versione di un file di testo in formato ini senza sezioni. Le informazioni note all'IDE vengono archiviate all'inizio del file. Viene fornito un collegamento tra la procedura guidata chiamata dall'IDE e i parametri presenti nel file con estensione vsz da passare all'IDE. Il resto del file fornisce parametri specifici della procedura guidata e che devono essere raccolti dall'IDE e passati alla procedura guidata specifica.  
  
 Nell'esempio seguente viene illustrato il contenuto di un file con estensione vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Di seguito sono riportate le parti del file con estensione vsz.  
  
|Parte|Descrizione|  
|----------|-----------------|  
|VSWizard|Il primo parametro nel file è il numero di versione del formato del file modello. Il numero di versione deve essere 6,0, 7,0, 7,1 o 8,0. Non è possibile avviare altri numeri e causare un errore di formato non valido.|  
|Procedura guidata|Questo campo contiene il ProgID OLE della procedura guidata o in alternativa una rappresentazione di stringa GUID del CLSID della procedura guidata creata dall'IDE.|  
|Param|Queste parti sono facoltative. È possibile aggiungere il numero desiderato.|  
  
 I parametri consentono al file con estensione VSZ di passare parametri personalizzati aggiuntivi alla procedura guidata. Ogni valore viene passato come elemento stringa in una matrice di varianti alla procedura guidata. Per ulteriori informazioni, vedere [parametri personalizzati](../../extensibility/internals/custom-parameters.md). Per informazioni sull'utilizzo di un file con estensione vsz nello sviluppo di procedure guidate personalizzate, vedere [. File VSZ (controllo progetto)](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 Per aggiungere un ID delle impostazioni locali predefinito al file con estensione vsz, specificare `FALLBACK_LCID` = xxxx, dove xxxx è l'ID delle impostazioni locali, ad esempio 1033 per l'inglese. Quando il `FALLBACK_LCID` parametro è definito, la procedura guidata usa l'ID delle impostazioni locali di fallback specificato se l'ID corrente non viene trovato.  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
