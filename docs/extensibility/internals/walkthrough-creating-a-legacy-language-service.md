---
title: 'Procedura dettagliata: creazione di un servizio di linguaggio Legacy Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703694"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procedura dettagliata: Creazione di un servizio di linguaggio legacy
L'uso delle classi di linguaggio MPF (Managed Package Framework) per implementare un servizio di linguaggio è [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] semplice. È necessario un pacchetto VSPackage per ospitare il servizio di linguaggio, il servizio di linguaggio stesso e un parser per il linguaggio.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio
 Il modello di progetto di pacchetto di Visual Studio è disponibile in tre diversi percorsi di modello nella finestra di dialogo **Nuovo progetto:The** Visual Studio Package Project Template can be found in three different template locations in the New Project dialog box:

1. Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.

2. Nella sezione relativa all'estendibilità di C#. Il linguaggio predefinito del progetto è C#.

3. Nella sezione relativa all'estendibilità di altri tipi di progetto. Il linguaggio predefinito del progetto è C++.

### <a name="create-a-vspackage"></a>Creare un pacchetto VSPackageCreate a VSPackage

1. Creare un nuovo pacchetto VSPackage con il modello di progetto di pacchetto di Visual Studio.Create a new VSPackage with the Visual Studio Package project template.

    Se si aggiunge un servizio di linguaggio a un VSPackage esistente, ignorare i passaggi seguenti e passare direttamente alla routine "Creare la classe del servizio di linguaggio".

2. Immettere MyLanguagePackage come nome del progetto e fare clic su **OK**.

    Puoi usare qualsiasi nome tu voglia. Queste procedure descritte di seguito presuppongono MyLanguagePackage come nome.

3. Selezionare [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] come lingua e l'opzione per generare un nuovo file di chiave. Fare clic su **Avanti**.

4. Immettere le informazioni appropriate sulla società e sul pacchetto. Fare clic su **Avanti**.

5. Selezionare **Comando di menu**. Fare clic su **Avanti**.

    Se non si intende supportare frammenti di codice, è sufficiente fare clic su Fine e ignorare il passaggio successivo.

6. Immettere **Inserisci frammento di codice** come nome del **comando** e `cmdidInsertSnippet` per ID **comando**. Fare clic su **Fine**.

    Il **nome del comando** e **l'ID di comando** possono essere quello che vuoi, questi sono solo esempi.

### <a name="create-the-language-service-class"></a>Creare la classe del servizio di linguaggioCreate the Language Service Class

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto MyLanguagePackage, **scegliere Aggiungi**, **Riferimento**, quindi scegliere il pulsante Aggiungi **nuovo riferimento** .

2. Nella finestra di dialogo **Aggiungi riferimento** selezionare **Microsoft.VisualStudio.Package.LanguageService** nella scheda **.NET** e fare clic su **OK**.

     Questa operazione deve essere eseguita una sola volta per il progetto di pacchetto di linguaggio.

3. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto VSPackage e scegliere **Aggiungi**, **Classe**.

4. Assicurarsi che **Classe** sia selezionato nell'elenco dei modelli.

5. Immettere **MyLanguageService.cs** nome del file di classe e fare clic su **Aggiungi**.

     Puoi usare qualsiasi nome tu voglia. Queste procedure descritte `MyLanguageService` in dettaglio si presuppongono il nome.

6. Nel file di MyLanguageService.cs `using` aggiungere le direttive seguenti.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modificare `MyLanguageService` la classe in <xref:Microsoft.VisualStudio.Package.LanguageService> modo che derivi dalla classe:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Posizionare il cursore su "LanguageService" e scegliere **Implementa classe astratta**dal menu **Modifica**, **IntelliSense** . In questo modo vengono aggiunti i metodi minimi necessari per implementare una classe del servizio di linguaggio.

9. Implementare i metodi astratti come descritto in [Implementazione di un servizio](../../extensibility/internals/implementing-a-legacy-language-service2.md)di linguaggio Legacy .

### <a name="register-the-language-service"></a>Registrare il servizio di linguaggioRegister the Language Service

1. Aprire il file di `using` MyLanguagePackagePackage.cs e aggiungere le direttive seguenti:Open the file MyLanguagePackagePackage.cs file and add the following directives:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Registrare la classe del servizio di linguaggio come descritto in [Registering a Legacy Language Service](../../extensibility/internals/registering-a-legacy-language-service1.md). Sono inclusi gli attributi ProvideXX e le sezioni "Proffering the Language Service". Utilizzare MyLanguageService in cui in questo argomento viene utilizzato TestLanguageService.Use MyLanguageService where this topic uses TestLanguageService.

### <a name="the-parser-and-scanner"></a>Il parser e lo scanner

1. Implementare un parser e uno scanner per il linguaggio in uso, come descritto in [Legacy Language Service Parser and Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     La modalità di implementazione del parser e dello scanner è interamente a voi e non rientra nell'ambito di questo argomento.

## <a name="language-service-features"></a>Funzionalità del servizio di linguaggio
 Per implementare ogni funzionalità nel servizio di linguaggio, in genere derivare una classe dalla classe del servizio di linguaggio MPF appropriata, implementare i metodi astratti in base alle esigenze ed eseguire l'override dei metodi appropriati. Le classi create e/o da cui derivate dipendono dalle funzionalità che si intende supportare. Queste funzionalità sono descritte in dettaglio in [Legacy Language Service Features](../../extensibility/internals/legacy-language-service-features1.md). La procedura seguente è l'approccio generale per derivare una classe dalle classi MPF.

#### <a name="deriving-from-an-mpf-class"></a>Derivazione da una classe MPFDeriving From an MPF Class

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto VSPackage e scegliere **Aggiungi**, **Classe**.

2. Assicurarsi che **Classe** sia selezionato nell'elenco dei modelli.

     Immettere un nome appropriato per il file di classe e fare clic su **Aggiungi**.

3. Nel nuovo file di classe `using` aggiungere le direttive seguenti.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modificare la classe in modo che derivi dalla classe MPF desiderata.

5. Aggiungere un costruttore di classe che accetta almeno gli stessi parametri del costruttore della classe base e passare i parametri del costruttore al costruttore della classe base.

     Ad esempio, il costruttore per <xref:Microsoft.VisualStudio.Package.Source> una classe derivata dalla classe potrebbe essere simile al seguente:For example, the constructor for a class derived from the class might look like the following:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Dal menu **Modifica**, **IntelliSense** , selezionare **Implementa classe astratta** se la classe base dispone di metodi astratti che devono essere implementati.

7. In caso contrario, posizionare il punto di inserimento all'interno della classe e immettere il metodo da sostituire.

     Ad esempio, `public override` digitare per visualizzare un elenco di tutti i metodi che possono essere sottoposti a override in tale classe.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
