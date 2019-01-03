---
title: 'Procedura: Creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9a954c00c616ff156d786386c92d41dcbe85c13
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818326"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Procedura: Creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild
  È possibile compilare, pulire e convalidare un pacchetto di SharePoint (*wsp*) usando le attività della riga di comando di MSBuild in un computer di sviluppo. È anche possibile usare questi comandi per automatizzare il processo di compilazione mediante Team Foundation Server in un computer di compilazione.  
  
## <a name="build-a-sharepoint-package"></a>Creare un pacchetto di SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Per compilare un pacchetto di SharePoint  
  
1.  Nella finestra di Windows **avviare** menu, scegliere **tutti i programmi** > **Accessori** > **prompt dei comandi**.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per creare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei comandi seguenti per creare un progetto di SharePoint denominato ListDefinition1 il pacchetto.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>Eliminare un pacchetto di SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Per eliminare un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per eliminare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei comandi seguenti per eliminare un progetto di SharePoint denominato ListDefinition1.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>Convalidare un pacchetto di SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Per convalidare un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per convalidare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei comandi seguenti per convalidare un progetto di SharePoint denominato ListDefinition1.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>Impostare le proprietà in un pacchetto di SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Per impostare una proprietà in un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per impostare una proprietà in un pacchetto per il progetto. Sostituire *PropertyName* con la proprietà che si desidera impostare.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per impostare il livello di avviso.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Vedere anche
 [Creare funzionalità di SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: Personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
