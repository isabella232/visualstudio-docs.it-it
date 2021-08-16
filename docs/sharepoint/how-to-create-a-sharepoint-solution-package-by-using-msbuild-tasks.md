---
title: Creare SharePoint pacchetto della soluzione usando MSBuild attività
description: Informazioni su come compilare, pulire e convalidare un pacchetto della soluzione SharePoint (con estensione wsp) usando le attività della riga di comando MSBuild in un computer di sviluppo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e35c4d407f9a09af2714ece6972fcb9e76595e0d0dc59c680a82dbb2ec776f86
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367616"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Procedura: Creare un pacchetto SharePoint di soluzioni usando MSBuild attività
  È possibile compilare, pulire e convalidare un pacchetto di SharePoint (*.wsp*) usando la riga di comando MSBuild in un computer di sviluppo. È anche possibile usare questi comandi per automatizzare il processo di compilazione usando Team Foundation Server in un computer di compilazione.

## <a name="build-a-sharepoint-package"></a>Compilare un pacchetto SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Per compilare un pacchetto SharePoint

1. Nel menu Windows **menu Start** scegliere Tutti **i programmi** Prompt dei  >  **comandi**  >  **accessori**.

2. Passare alla directory in cui si trova SharePoint progetto.

3. Immettere il comando seguente per creare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Ad esempio, è possibile eseguire uno dei comandi seguenti per creare un pacchetto SharePoint progetto denominato ListDefinition1.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Pulire un pacchetto SharePoint

#### <a name="to-clean-a-sharepoint-package"></a>Per pulire un pacchetto SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova SharePoint progetto.

3. Immettere il comando seguente per pulire un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Ad esempio, è possibile eseguire uno dei comandi seguenti per pulire SharePoint progetto denominato ListDefinition1.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Convalidare un SharePoint distribuzione

#### <a name="to-validate-a-sharepoint-package"></a>Per convalidare un pacchetto SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova SharePoint progetto.

3. Immettere il comando seguente per convalidare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Ad esempio, è possibile eseguire uno dei comandi seguenti per convalidare SharePoint progetto denominato ListDefinition1.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Impostare le proprietà in un pacchetto SharePoint distribuzione

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Per impostare una proprietà in un pacchetto SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova SharePoint progetto.

3. Immettere il comando seguente per impostare una proprietà in un pacchetto per il progetto. Sostituire *PropertyName* con la proprietà che si vuole impostare.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Ad esempio, è possibile eseguire il comando seguente per impostare il livello di avviso.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Vedi anche
- [Creare SharePoint funzionalità](../sharepoint/creating-sharepoint-features.md)
- [Procedura: Personalizzare una funzionalità SharePoint personalizzata](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: Aggiungere e rimuovere elementi in SharePoint funzionalità](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
