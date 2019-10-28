---
title: Uso di moduli per includere file nella soluzione | Microsoft Docs
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
ms.openlocfilehash: 4f8f2aa6c5d86af2424a811b6167829cefdb6fb5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985299"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Usare i moduli per includere i file nella soluzione
  In alcuni casi potrebbe essere necessario distribuire i file nel server SharePoint indipendentemente dal tipo di file, ad esempio le nuove pagine master. A tale scopo, è possibile usare i *moduli* (da non confondere con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli di codice). I moduli sono contenitori per i file in una soluzione SharePoint. Quando la soluzione viene distribuita, i file del modulo vengono copiati nelle cartelle specificate sul server SharePoint.

## <a name="module-items-and-elements"></a>Elementi e elementi del modulo
 Per creare un modulo, aggiungerlo a un progetto selezionandolo nella finestra di dialogo **Aggiungi nuovo elemento** . Modificare quindi il file *Elements. XML* in modo da includere i nomi dei file che si desidera distribuire, dove si trovano nel sistema e dove devono essere copiati nel server SharePoint.

 Di seguito è riportato un esempio del file *Elements. XML* per un modulo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 I moduli appena creati contengono i file predefiniti seguenti:

|Nome file|Descrizione|
|---------------|-----------------|
|*Elements. XML*|Il file di definizione per il modulo.|
|*Sample. txt*|File segnaposto che funge da esempio di file nel modulo.|

 Il file *Elements. XML* contiene gli elementi seguenti:

|Nome elemento|Descrizione|
|------------------|-----------------|
|Elementi|Contiene tutti gli elementi definiti nel modulo.|
|Modulo|L'elemento Module ha un solo attributo, *Name*, che specifica il nome del modulo nel formato `<Module Name="Module1">`.<br /><br /> Si noti che se si modifica il nome del modulo (o della relativa proprietà *nome cartella* ), è necessario aggiornare manualmente il nome nell'elemento Module.<br /><br /> Se si specifica una sottodirectory per i file nell'elemento modulo, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) creerà automaticamente una struttura di directory corrispondente.|
|File|L'elemento file ha due parametri, *path* e *URL*.<br /><br /> -Path: il nome e il percorso del file nella soluzione SharePoint. Il formato è, `Path="Module1\Sample.txt"`.<br /><br /> -URL: percorso in cui verrà distribuito il file nel server SharePoint. Il formato è, `Url="Module1/Sample.txt"`.<br /><br /> -Type: attributo facoltativo con due impostazioni: *GhostableInLibrary* e *Ghostable*. Il formato è, `Type="GhostableInLibrary"`. Se si specifica *GhostableInLibrary* , il file verrà aggiunto a una raccolta documenti in SharePoint insieme a una voce di elenco che accompagna il file quando viene aggiunto alla libreria. L'impostazione di *Ghostable* comporta l'aggiunta del file a SharePoint all'esterno della raccolta documenti.|

 Ogni file che si desidera distribuire richiede una voce di elemento `<File>` separata in *Elements. XML*.

## <a name="see-also"></a>Vedere anche
- [Procedura: includere file mediante un modulo](../sharepoint/how-to-include-files-by-using-a-module.md)
- [procedura: effettuare il provisioning di un file](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
