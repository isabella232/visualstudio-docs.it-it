---
title: Personalizzare SharePoint pacchetto della soluzione usando MSBuild destinazioni
titleSuffix: ''
description: Personalizzare la Visual Studio di SharePoint file del pacchetto della soluzione (con estensione wsp) usando MSBuild al prompt dei comandi.
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
ms.openlocfilehash: 998bcd8ca191e5d7f5c3868836b4c498cae563c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106744"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Procedura: Personalizzare un pacchetto SharePoint soluzione di distribuzione usando MSBuild destinazioni
  Usando le MSBuild al prompt dei comandi, è possibile personalizzare la modalità di creazione Visual Studio file SharePoint pacchetto (*con estensione wsp*). Ad esempio è possibile personalizzare le proprietà di MSBuild per modificare la directory intermedia dei pacchetti e i gruppi di elementi di MSBuild con cui si specificano i file enumerati.

## <a name="customize-and-run-msbuild-targets"></a>Personalizzare ed eseguire MSBuild destinazione
 Se si personalizzano le destinazioni di BeforeLayout e AfterLayout, è possibile eseguire le attività prima del layout del pacchetto, ad esempio aggiungendo, rimuovendo o modificando i file che verranno inclusi nel pacchetto.

#### <a name="to-customize-the-beforelayout-target"></a>Per personalizzare la destinazione BeforeLayout

1. Aprire un editor, ad esempio Blocco note, quindi aggiungere il codice riportato di seguito.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    In questo esempio viene visualizzato un messaggio prima della creazione del pacchetto di questa destinazione.

2. Assegnare al file il nome **CustomLayout.SharePoint.targets** e quindi salvarlo nella cartella per il SharePoint progetto.

3. Aprire il progetto, aprire il relativo menu di scelta rapida e quindi **scegliere Scarica Project**.

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e quindi scegliere **Modifica** *\<ProjectName> .vbproj* **o Modifica** *\<ProjectName> .csproj.*

5. Dopo la riga `Import` verso la fine del file di progetto, aggiungere la seguente riga.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Salva e chiudi il file di progetto.

7. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e quindi scegliere **Ricarica Project**.

   Quando si pubblica il progetto, il messaggio viene visualizzato nell'output prima che inizi la creazione del pacchetto.

#### <a name="to-customize-the-afterlayout-target"></a>Per personalizzare la destinazione AfterLayout

1. Sulla barra dei menu scegliere **Apri**  >    >  **file.**

2. Nella finestra **di dialogo** Apri file passare alla cartella del progetto, scegliere il file CustomLayout.target e quindi scegliere il **pulsante** Apri.

3. Prima del tag `</Project>` aggiungere il codice seguente:

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    In questo esempio viene visualizzato un messaggio dopo la creazione del pacchetto di questa destinazione.

4. Salvare e chiudere il file di destinazioni.

5. Riavviare Visual Studio, quindi aprire il progetto.

   Quando si pubblica il progetto, il messaggio di BeforeLayout viene visualizzato prima che inizi la creazione del pacchetto e il messaggio di AfterLayout viene visualizzato al termine della creazione del pacchetto.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
