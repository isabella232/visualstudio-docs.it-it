---
title: 'Procedura dettagliata: Creazione di un servizio di linguaggio Legacy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d58234dbe503f8d086e081464c2e38f759a75e3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067092"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procedura dettagliata: Creazione di un servizio di linguaggio legacy
Utilizzando le classi di linguaggio framework (MPF) di pacchetto gestito per implementare un servizio di linguaggio in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] è semplice. È necessario un pacchetto VSPackage per ospitare il servizio di linguaggio, il servizio di linguaggio stesso e un parser per la propria lingua.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio
 Il modello di progetto di Visual Studio pacchetto sono reperibili in tre posizioni di modelli diversi nella **nuovo progetto** nella finestra di dialogo:

1. Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.

2. Nella sezione relativa all'estendibilità di C#. Il linguaggio predefinito del progetto è C#.

3. Nella sezione relativa all'estendibilità di altri tipi di progetto. Il linguaggio predefinito del progetto è C++.

### <a name="create-a-vspackage"></a>Creare un pacchetto VSPackage

1. Creare un nuovo pacchetto di Visual Studio con il modello di progetto di pacchetto di Visual Studio.

    Se si aggiunge un servizio di linguaggio a un pacchetto esistente, ignorare i passaggi seguenti e passare direttamente alla procedura "Creare la classe di servizio del linguaggio".

2. Immettere MyLanguagePackage per il nome del progetto e fare clic su **OK**.

    È possibile usare qualsiasi nome desiderato. Queste procedure descritti in questa sezione presuppongono MyLanguagePackage come nome.

3. Selezionare [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] come il linguaggio e l'opzione per generare un nuovo file di chiave. Scegliere **Avanti**.

4. Immettere le informazioni aziendali e pacchetto appropriate. Scegliere **Avanti**.

5. Selezionare **comando di Menu**. Scegliere **Avanti**.

    Se non si intende supportare frammenti di codice, è possibile semplicemente fare clic su Fine e ignorare il passaggio successivo.

6. Immettere **Inserisci frammento** come la **nome del comando** e `cmdidInsertSnippet` per i **ID di comando**. Scegliere **Fine**.

    Il **nome del comando** e **ID comando** può essere qualsiasi elemento, questi sono solo esempi.

### <a name="create-the-language-service-class"></a>Creare la classe di servizio di linguaggio

1. Nella **Esplora soluzioni**, pulsante destro del mouse sul progetto MyLanguagePackage, scegliere **Add**, **riferimento**, quindi scegliere il **Aggiungi nuovo riferimento** pulsante.

2. Nel **Aggiungi riferimento** finestra di dialogo **Microsoft.VisualStudio.Package.LanguageService** nel **.NET** scheda e fare clic su **OK**.

     Questa operazione deve essere eseguito solo una volta per il progetto di pacchetto di linguaggio.

3. Nelle **Esplora soluzioni**, fare clic destro sul progetto VSPackage e selezionare **Add**, **classe**.

4. Assicurarsi che **classe** sia selezionato nell'elenco dei modelli.

5. Immettere **MyLanguageService.cs** per il nome del file di classe e fare clic su **Add**.

     È possibile usare qualsiasi nome desiderato. Queste procedure descritti in questa sezione presuppongono `MyLanguageService` come nome.

6. Aggiungere il codice seguente nel file MyLanguageService.cs `using` istruzioni.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modificare il `MyLanguageService` classe da cui derivare il <xref:Microsoft.VisualStudio.Package.LanguageService> classe:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Posizionare il cursore su "LanguageService" e dal **Edit**, **IntelliSense** dal menu **implementa classe astratta**. Aggiunge il numero minimo di metodi necessario per implementare una classe di servizio di linguaggio.

9. Implementare i metodi astratti, come descritto nella [implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Registrare il servizio di linguaggio

1. Aprire il file MyLanguagePackagePackage.cs e aggiungere il codice seguente `using` istruzioni:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Registrare la classe di servizio di linguaggio, come descritto in [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md). Ciò include gli attributi di ProvideXX e nelle sezioni "Proffering del servizio di linguaggio". Usare MyLanguageService in questo argomento Usa TestLanguageService.

### <a name="the-parser-and-scanner"></a>Il Parser e Scanner

1. Implementare un parser e scanner per il linguaggio, come descritto nella [Scanner e Parser servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Come si implementa il parser e lo scanner è completamente responsabilità dell'utente e rientra nell'ambito di questo argomento.

## <a name="language-service-features"></a>Funzionalità del linguaggio del servizio
 Per implementare ogni funzionalità servizio di linguaggio, in genere una classe derivata dalla classe di servizio del linguaggio MPF appropriata, implementare eventuali metodi astratti in base alle esigenze ed eseguire l'override dei metodi appropriati. Quali classi creare e/o derivare da dipende dalle funzionalità di cui si intende supportare. Queste funzionalità sono illustrate dettagliatamente [funzionalità del servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-features1.md). La procedura seguente è l'approccio generale per la derivazione di una classe dalle classi di MPF.

#### <a name="deriving-from-an-mpf-class"></a>Derivazione da una classe MPF

1. Nelle **Esplora soluzioni**, fare clic destro sul progetto VSPackage e selezionare **Add**, **classe**.

2. Assicurarsi che **classe** sia selezionato nell'elenco dei modelli.

     Immettere un nome appropriato per il file di classe e fare clic su **Add**.

3. Nel nuovo file di classe, aggiungere il codice seguente `using` istruzioni.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modificare la classe da cui derivare la classe MPF desiderata.

5. Aggiungere un costruttore di classe che accetta almeno gli stessi parametri del costruttore della classe di base e passare i parametri del costruttore al costruttore della classe base.

     Ad esempio, il costruttore per una classe derivata dal <xref:Microsoft.VisualStudio.Package.Source> classe potrebbe avere un aspetto simile al seguente:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Dal **Edit**, **IntelliSense** dal menu **implementa classe astratta** se la classe di base dispone di metodi astratti che devono essere implementati.

7. In caso contrario, posizionare il cursore all'interno della classe e immettere il metodo da sottoporre a override.

     Ad esempio, digitare `public override` per visualizzare un elenco di tutti i metodi che possono essere sostituite in tale classe.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)