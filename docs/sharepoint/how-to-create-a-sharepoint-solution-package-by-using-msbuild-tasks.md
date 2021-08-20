---
title: Creare SharePoint pacchetto della soluzione usando MSBuild attività
description: Informazioni su come compilare, pulire e convalidare un pacchetto SharePoint soluzione (con estensione wsp) usando le attività MSBuild riga di comando in un computer di sviluppo.
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
ms.openlocfilehash: 781281c6abce5031166b00d9cdde0b175619f79b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135923"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Procedura: Creare un pacchetto SharePoint soluzione usando MSBuild attività
  È possibile compilare, pulire e convalidare un pacchetto SharePoint ( con estensione *wsp*) usando la riga di MSBuild in un computer di sviluppo. È anche possibile usare questi comandi per automatizzare il processo di compilazione usando Team Foundation Server in un computer di compilazione.

## <a name="build-a-sharepoint-package"></a>Compilare un pacchetto SharePoint distribuzione

#### <a name="to-build-a-sharepoint-package"></a>Per compilare un pacchetto SharePoint

1. Nel menu Windows **Start** scegliere Prompt dei comandi Tutti **i**  >  **programmi**  >  **Accessori**.

2. Passare alla directory in cui si trova SharePoint progetto.

3. Immettere il comando seguente per creare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Ad esempio, è possibile eseguire uno dei comandi seguenti per creare un pacchetto di un SharePoint denominato ListDefinition1.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Pulire un pacchetto SharePoint distribuzione

#### <a name="to-clean-a-sharepoint-package"></a>Per pulire un pacchetto SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova SharePoint progetto.

3. Immettere il comando seguente per pulire un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Ad esempio, è possibile eseguire uno dei comandi seguenti per pulire un SharePoint denominato ListDefinition1.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Convalidare un SharePoint personalizzato

#### <a name="to-validate-a-sharepoint-package"></a>Per convalidare un pacchetto SharePoint

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory in cui si trova SharePoint progetto.

3. Immettere il comando seguente per convalidare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Ad esempio, è possibile eseguire uno dei comandi seguenti per convalidare un SharePoint denominato ListDefinition1.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Impostare le proprietà in un SharePoint pacchetto

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
- [Procedura: Personalizzare una SharePoint personalizzata](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: Aggiungere e rimuovere elementi per SharePoint funzionalità](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
