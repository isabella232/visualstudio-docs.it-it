---
title: Personalizzare il pacchetto della soluzione SharePoint tramite destinazioni MSBuild
titleSuffix: ''
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
ms.openlocfilehash: 9845f755d184c18b6b5ade4c5504e393edae7b00
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585810"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Procedura: personalizzare un pacchetto della soluzione SharePoint tramite destinazioni MSBuild
  Utilizzando le destinazioni di MSBuild a un prompt dei comandi, è possibile personalizzare la modalità di creazione dei file del pacchetto SharePoint (con*estensione wsp*) in Visual Studio. Ad esempio è possibile personalizzare le proprietà di MSBuild per modificare la directory intermedia dei pacchetti e i gruppi di elementi di MSBuild con cui si specificano i file enumerati.

## <a name="customize-and-run-msbuild-targets"></a>Personalizzare ed eseguire destinazioni MSBuild
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

2. Denominare il file **CustomLayout. SharePoint. targets**, quindi salvarlo nella cartella del progetto SharePoint.

3. Aprire il progetto, aprire il menu di scelta rapida e scegliere **Scarica progetto**.

4. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto, quindi scegliere **Edit** * \<ProjectName> . vbproj* o **Edit** * \<ProjectName> . csproj*.

5. Dopo la riga `Import` verso la fine del file di progetto, aggiungere la seguente riga.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Salva e chiudi il file di progetto.

7. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto, quindi scegliere **Ricarica progetto**.

   Quando si pubblica il progetto, il messaggio viene visualizzato nell'output prima che inizi la creazione del pacchetto.

#### <a name="to-customize-the-afterlayout-target"></a>Per personalizzare la destinazione AfterLayout

1. Nella barra dei menu scegliere **file**  >  **Apri**  >  **file**.

2. Nella finestra di dialogo **Apri file** passare alla cartella del progetto, scegliere il file customlayout. target, quindi scegliere il pulsante **Apri** .

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
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
