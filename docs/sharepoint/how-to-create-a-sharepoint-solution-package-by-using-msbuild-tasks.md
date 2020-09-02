---
title: Creazione di un pacchetto della soluzione SharePoint tramite le attività MSBuild
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c59a38e1153a57c1bd886121eeac244075045a42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017010"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Procedura: creare un pacchetto della soluzione SharePoint tramite le attività MSBuild
  È possibile compilare, pulire e convalidare un pacchetto di SharePoint (con*estensione wsp*) utilizzando le attività MSBuild della riga di comando in un computer di sviluppo. È inoltre possibile utilizzare questi comandi per automatizzare il processo di compilazione utilizzando Team Foundation Server in un computer di compilazione.

## <a name="build-a-sharepoint-package"></a>Creazione di un pacchetto di SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Per compilare un pacchetto di SharePoint

1. Dal menu **Start** di Windows scegliere **tutti i programmi**  >  **Accessori**  >  **prompt dei comandi**.

2. Passare alla directory in cui si trova il progetto SharePoint.

3. Immettere il comando seguente per creare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     È ad esempio possibile eseguire uno dei comandi seguenti per creare un pacchetto di un progetto SharePoint denominato ListDefinition1.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Pulire un pacchetto di SharePoint

#### <a name="to-clean-a-sharepoint-package"></a>Per pulire un pacchetto di SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova il progetto SharePoint.

3. Immettere il comando seguente per pulire un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     È ad esempio possibile eseguire uno dei comandi seguenti per pulire un progetto SharePoint denominato ListDefinition1.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Convalidare un pacchetto di SharePoint

#### <a name="to-validate-a-sharepoint-package"></a>Per convalidare un pacchetto di SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova il progetto SharePoint.

3. Immettere il comando seguente per convalidare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     È ad esempio possibile eseguire uno dei comandi seguenti per convalidare un progetto SharePoint denominato ListDefinition1.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Impostare le proprietà in un pacchetto di SharePoint

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Per impostare una proprietà in un pacchetto di SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova il progetto SharePoint.

3. Immettere il comando seguente per impostare una proprietà in un pacchetto per il progetto. Sostituire *PropertyName* con la proprietà che si desidera impostare.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Ad esempio, è possibile eseguire il comando seguente per impostare il livello di avviso.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Vedere anche
- [Creazione di funzionalità di SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Procedura: personalizzare una funzionalità di SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: aggiungere e rimuovere elementi nelle funzionalità di SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
