---
title: Uso di moduli per includere file nella soluzione | Microsoft Docs
description: Usare moduli o contenitori per i file in una soluzione SharePoint per distribuire i file nel server SharePoint indipendentemente dal tipo di file, ad esempio le pagine master.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9427f722354ba6ef7d1694e12bf176170cd969a346bd6b85420845a2ec0a410f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352861"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Usare i moduli per includere i file nella soluzione
  In alcuni casi può essere necessario distribuire file nel server SharePoint indipendentemente dal tipo di file, ad esempio le nuove pagine master. A tale scopo, è possibile usare *Moduli* (da non confondere con i [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli di codice). I moduli sono contenitori per i file in una SharePoint soluzione. Quando la soluzione viene distribuita, i file nel modulo vengono copiati nelle cartelle specificate nel server SharePoint.

## <a name="module-items-and-elements"></a>Elementi ed elementi del modulo
 Per creare un modulo, aggiungerlo a un progetto scegliendolo nella finestra **di** dialogo Aggiungi nuovo elemento. Modificare quindi il file *Elements.xml* in modo da includere i nomi dei file da distribuire, la posizione in cui si trovano nel sistema e la posizione in cui devono essere copiati nel server SharePoint.

 Di seguito è riportato un esempio del file *Elements.xml* per un modulo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 I moduli appena creati contengono i file predefiniti seguenti:

|File Name|Descrizione|
|---------------|-----------------|
|*Elements.xml*|File di definizione per il modulo.|
|*Sample.txt*|Un file segnaposto che funge da esempio di file nel modulo.|

 Il *Elements.xml* file contiene gli elementi seguenti:

|Nome dell'elemento|Descrizione|
|------------------|-----------------|
|Elementi|Contiene tutti gli elementi definiti nel modulo.|
|Modulo|L'elemento module ha un singolo attributo, *Name,* che specifica il nome del modulo nel formato `<Module Name="Module1">` .<br /><br /> Si noti che se si modifica il nome del modulo (o la relativa proprietà *Folder Name),* è necessario aggiornare manualmente il nome nell'elemento Module.<br /><br /> Se si specifica una sottodirectory per i file nell'elemento Module, (WSS) creerà automaticamente una struttura di [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] directory corrispondente.|
|File|L'elemento File ha due parametri, *Path* e *Url.*<br /><br /> - Percorso: il nome e il percorso del file nella SharePoint soluzione. Il formato è `Path="Module1\Sample.txt"` .<br /><br /> - URL: percorso in cui verrà distribuito il file nel server SharePoint. Il formato è `Url="Module1/Sample.txt"` .<br /><br /> - Tipo: attributo facoltativo con due impostazioni: *GhostableInLibrary* e *Ghostable.* Il formato è `Type="GhostableInLibrary"` . Se si *specifica GhostableInLibrary,* il file verrà aggiunto a una raccolta documenti in SharePoint insieme a un elemento elenco associato al file quando viene aggiunto alla raccolta. Se si *specifica Ghostable,* il file viene aggiunto SharePoint all'esterno della raccolta documenti.|

 Ogni file che si vuole distribuire richiede una voce `<File>` di elemento separata in *Elements.xml*.

## <a name="see-also"></a>Vedi anche
- [Procedura: Includere file usando un modulo](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Procedura: Effettuare il provisioning di un file](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Sviluppo di SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md)
- [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
