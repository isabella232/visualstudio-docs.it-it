---
title: Uso dei moduli per includere i file nella soluzione | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7fe8572ea5ac6f2c100d203063dd43b02c78749b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864189"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Usare i moduli per includere file nella soluzione
  Potrebbe esserci situazioni quando si vuole distribuire i file nel server di SharePoint indipendentemente dal loro tipo di file, ad esempio nuove pagine master. A tale scopo, è possibile usare *moduli* (non deve essere confusa con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli di codice). I moduli sono contenitori per i file in una soluzione di SharePoint. Quando si distribuisce la soluzione, i file nel modulo vengono copiati nelle cartelle specificate nel server SharePoint.  
  
## <a name="module-items-and-elements"></a>Elementi del modulo
 Per creare un modulo, aggiungerlo a un progetto scegliendolo nella **Aggiungi nuovo elemento** nella finestra di dialogo. Modificare quindi relativi *Elements* file da includere i nomi dei file di cui si vuole distribuire, in cui si trovano nel sistema e devono essere copiati nel server SharePoint.  
  
 Di seguito è riportato un esempio del *Elements* file per un modulo:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Nuovi moduli contengono i file predefiniti seguenti:  
  
|Nome file|Descrizione|  
|---------------|-----------------|  
|*Elements.xml*|File di definizione per il modulo.|  
|*Sample.txt*|Un file segnaposto che funge da un esempio di un file nel modulo.|  
  
 Il *Elements* file contiene gli elementi seguenti:  
  
|Nome elemento|Descrizione|  
|------------------|-----------------|  
|Elementi|Contiene tutti gli elementi definiti nel modulo.|  
|Modulo|L'elemento di modulo ha un solo attributo, *Name*, che specifica il nome del modulo nel formato `<Module Name="Module1">`.<br /><br /> Si noti che se si modifica il nome del modulo (o dai relativi *nome cartella* proprietà), è necessario aggiornare manualmente il nome dell'elemento di modulo.<br /><br /> Se si specifica una sottodirectory per i file nell'elemento del modulo, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) creerà automaticamente una struttura di directory corrispondente per loro.|  
|File|L'elemento File ha due parametri, *tracciato* e *Url*.<br /><br /> -Path: Il nome e percorso del file della soluzione di SharePoint. Il formato è, `Path="Module1\Sample.txt"`.<br /><br /> -Url: Il percorso in cui verrà distribuito il file nel server SharePoint. Il formato è, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Attributo facoltativo che ha due impostazioni: *GhostableInLibrary* e *Ghostable*. Il formato è, `Type="GhostableInLibrary"`. Che specifica *GhostableInLibrary* significa che il file verrà aggiunto a una raccolta documenti di SharePoint insieme a un elemento di elenco associata al file quando viene aggiunto alla raccolta. Che specifica *Ghostable* fa sì che il file viene aggiunto a SharePoint all'esterno della raccolta documenti.|  
  
 Ogni file che si desidera distribuire richiede un oggetto separato `<File>` voce elemento nel *Elements*.  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Includere file mediante un modulo](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [Come si fa: Effettuare il provisioning di un file](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
