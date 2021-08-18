---
title: 'Procedura dettagliata: Creazione di un servizio di linguaggio legacy | Microsoft Docs'
description: Informazioni su come usare le classi del linguaggio del framework del pacchetto gestito per implementare un servizio di linguaggio in Visual C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a0f3e497368047cec2ce1518e7b01f59a8895fbc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110449"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procedura dettagliata: Creazione di un servizio di linguaggio legacy
L'uso delle classi di linguaggio MPF (Managed Package Framework) per implementare un servizio di linguaggio in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] è semplice. È necessario un VSPackage per ospitare il servizio di linguaggio, il servizio di linguaggio stesso e un parser per il linguaggio.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK.](../../extensibility/visual-studio-sdk.md)

## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio
 Il Visual Studio modello Project pacchetto è disponibile in tre posizioni diverse per i modelli nella finestra **di dialogo Project** nuova versione:

1. Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.

2. Nella sezione relativa all'estendibilità di C#. Il linguaggio predefinito del progetto è C#.

3. Nella sezione relativa all'estendibilità di altri tipi di progetto. Il linguaggio predefinito del progetto è C++.

### <a name="create-a-vspackage"></a>Creare un pacchetto VSPackage

1. Creare un nuovo PACCHETTO VSPackage con il Visual Studio di progetto Pacchetto.

    Se si aggiunge un servizio di linguaggio a un VSPackage esistente, ignorare i passaggi seguenti e passare direttamente alla procedura "Creare la classe del servizio di linguaggio".

2. Immettere MyLanguagePackage come nome del progetto e fare clic su **OK.**

    È possibile usare qualsiasi nome. Queste procedure descritte in dettaglio presuppongono MyLanguagePackage come nome.

3. Selezionare [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] come lingua e l'opzione per generare un nuovo file di chiave. Fare clic su **Avanti**.

4. Immettere le informazioni appropriate sulla società e sul pacchetto. Fare clic su **Avanti**.

5. Selezionare **Comando di menu**. Fare clic su **Avanti**.

    Se non si intende supportare frammenti di codice, è sufficiente fare clic su Fine e ignorare il passaggio successivo.

6. Immettere **Inserisci frammento** come **Nome comando e** per ID `cmdidInsertSnippet` **comando**. Fare clic su **Fine**.

    Il **nome del comando** e **l'ID** comando possono essere qualsiasi cosa si voglia. Questi sono solo esempi.

### <a name="create-the-language-service-class"></a>Creare la classe del servizio di linguaggio

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto MyLanguagePackage, scegliere **Aggiungi** **,** Riferimento **e** quindi fare clic sul pulsante **Aggiungi nuovo** riferimento.

2. Nella finestra **di dialogo Aggiungi** riferimento selezionare **Microsoft.VisualStudio.Package.LanguageService** nella scheda **.NET** e fare clic su **OK.**

     Questa operazione deve essere eseguita una sola volta per il progetto del pacchetto di linguaggio.

3. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto VSPackage e **scegliere Aggiungi**, **Classe**.

4. Assicurarsi che **l'opzione** Classe sia selezionata nell'elenco dei modelli.

5. Immettere **MyLanguageService.cs** come nome del file di classe e fare clic su **Aggiungi**.

     È possibile usare qualsiasi nome. Queste procedure descritte in dettaglio `MyLanguageService` presuppongono come nome.

6. Nel file MyLanguageService.cs aggiungere le `using` direttive seguenti.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet1":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet1":::

7. Modificare la `MyLanguageService` classe in modo che derivi dalla classe <xref:Microsoft.VisualStudio.Package.LanguageService> :

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet2":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet2":::

8. Posizionare il cursore su "LanguageService" e **scegliere** Implementa classe astratta dal menu Modifica , **IntelliSense.** In questo modo vengono aggiunti i metodi minimi necessari per implementare una classe del servizio di linguaggio.

9. Implementare i metodi astratti come descritto in [Implementazione di un servizio di linguaggio legacy.](../../extensibility/internals/implementing-a-legacy-language-service2.md)

### <a name="register-the-language-service"></a>Registrare il servizio di linguaggio

1. Aprire il file MyLanguagePackagePackage.cs e aggiungere le `using` direttive seguenti:

     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb" id="Snippet3":::
     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs" id="Snippet3":::

2. Registrare la classe del servizio di linguaggio come descritto in [Registrazione di un servizio di linguaggio legacy.](../../extensibility/internals/registering-a-legacy-language-service1.md) Sono inclusi gli attributi ProvideXX e le sezioni "Proffering the Language Service". Usare MyLanguageService in cui questo argomento usa TestLanguageService.

### <a name="the-parser-and-scanner"></a>Parser e scanner

1. Implementare un parser e uno scanner per il linguaggio, come descritto in Parser e scanner del [servizio di linguaggio legacy.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

     La modalità di implementazione del parser e dello scanner dipende interamente dall'utente e non è in linea con l'ambito di questo argomento.

## <a name="language-service-features"></a>Funzionalità del servizio di linguaggio
 Per implementare ogni funzionalità nel servizio di linguaggio, in genere si deriva una classe dalla classe del servizio di linguaggio MPF appropriata, si implementano i metodi astratti in base alle esigenze ed si esegue l'override dei metodi appropriati. Le classi create e/o derivate da dipendono dalle funzionalità che si intende supportare. Queste funzionalità sono descritte in dettaglio in [Funzionalità del servizio di linguaggio legacy.](../../extensibility/internals/legacy-language-service-features1.md) La procedura seguente rappresenta l'approccio generale alla derivazione di una classe dalle classi MPF.

#### <a name="deriving-from-an-mpf-class"></a>Derivazione da una classe MPF

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto VSPackage e **scegliere Aggiungi**, **Classe**.

2. Assicurarsi che **l'opzione** Classe sia selezionata nell'elenco dei modelli.

     Immettere un nome appropriato per il file di classe e fare clic su **Aggiungi**.

3. Nel nuovo file di classe aggiungere le `using` direttive seguenti.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet4":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet4":::

4. Modificare la classe in modo che derivi dalla classe MPF desiderata.

5. Aggiungere un costruttore di classe che accetta almeno gli stessi parametri del costruttore della classe di base e passa i parametri del costruttore al costruttore della classe base.

     Ad esempio, il costruttore per una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Source> classe potrebbe essere simile al seguente:

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet5":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet5":::

6. Dal menu **Modifica**, **IntelliSense** selezionare Implementa classe astratta se la classe di base ha metodi astratti che devono essere implementati. 

7. In caso contrario, posizionare il cursore all'interno della classe e immettere il metodo da sottoporre a override.

     Ad esempio, digitare `public override` per visualizzare un elenco di tutti i metodi di cui è possibile eseguire l'override in tale classe.

## <a name="see-also"></a>Vedi anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
