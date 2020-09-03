---
title: 'Procedura dettagliata: creazione di un servizio di linguaggio legacy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbdad85dd1c0f62b22bb33b5ed6ab2c597e62164
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905992"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procedura dettagliata: Creazione di un servizio di linguaggio legacy
L'uso delle classi di linguaggio del Framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] è semplice. È necessario un pacchetto VSPackage per ospitare il servizio di linguaggio, il servizio di linguaggio e un parser per la lingua in uso.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio
 Il modello di progetto di pacchetto di Visual Studio è disponibile in tre diverse posizioni dei modelli nella finestra di dialogo **nuovo progetto** :

1. Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.

2. Nella sezione relativa all'estendibilità di C#. Il linguaggio predefinito del progetto è C#.

3. Nella sezione relativa all'estendibilità di altri tipi di progetto. Il linguaggio predefinito del progetto è C++.

### <a name="create-a-vspackage"></a>Creare un pacchetto VSPackage

1. Creare un nuovo pacchetto VSPackage con il modello di progetto di pacchetto di Visual Studio.

    Se si aggiunge un servizio di linguaggio a un VSPackage esistente, ignorare i passaggi seguenti e passare direttamente alla procedura "creare la classe del servizio di linguaggio".

2. Immettere MyLanguagePackage per il nome del progetto e fare clic su **OK**.

    È possibile usare il nome desiderato. Le procedure descritte in questo argomento presuppongono MyLanguagePackage come nome.

3. Selezionare [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] come lingua e l'opzione per generare un nuovo file di chiave. Fare clic su **Avanti**.

4. Immettere le informazioni sulla società e sul pacchetto appropriate. Fare clic su **Avanti**.

5. Selezionare il **comando di menu**. Fare clic su **Avanti**.

    Se non si intende supportare i frammenti di codice, è possibile fare semplicemente clic su fine e ignorare il passaggio successivo.

6. Immettere **snippet di inserimento** come **nome del comando** e `cmdidInsertSnippet` per l' **ID comando**. Fare clic su **Fine**.

    Il **nome del comando** e l' **ID di comando** possono essere tutti quelli desiderati. questi sono solo esempi.

### <a name="create-the-language-service-class"></a>Creazione della classe del servizio di linguaggio

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto MyLanguagePackage, scegliere **Aggiungi**, **riferimento**, quindi scegliere il pulsante **Aggiungi nuovo riferimento** .

2. Nella finestra di dialogo **Aggiungi riferimento** selezionare **Microsoft. VisualStudio. Package. LanguageService** nella scheda **.NET** e fare clic su **OK**.

     Questa operazione deve essere eseguita una sola volta per il progetto Language Package.

3. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto VSPackage e scegliere **Aggiungi**, **classe**.

4. Assicurarsi che la **classe** sia selezionata nell'elenco modelli.

5. Immettere **MyLanguageService.cs** per il nome del file di classe e fare clic su **Aggiungi**.

     È possibile usare il nome desiderato. Queste procedure sono descritte `MyLanguageService` in dettaglio come nome.

6. Nel file MyLanguageService.cs aggiungere le `using` direttive seguenti.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modificare la `MyLanguageService` classe per derivare dalla <xref:Microsoft.VisualStudio.Package.LanguageService> classe:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Posizionare il cursore su "LanguageService" e scegliere **implementa classe astratta**dal menu **modifica**, **IntelliSense** . In questo modo vengono aggiunti i metodi minimi necessari per implementare una classe del servizio di linguaggio.

9. Implementare i metodi astratti come descritto in [implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Registrare il servizio di linguaggio

1. Aprire il file MyLanguagePackagePackage.cs e aggiungere le `using` direttive seguenti:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Registrare la classe del servizio di linguaggio come descritto in [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md). Sono inclusi gli attributi ProvideXX e le sezioni "profondendo The Language Service". Utilizzare MyLanguageService in cui questo argomento utilizza TestLanguageService.

### <a name="the-parser-and-scanner"></a>Parser e scanner

1. Implementare un parser e uno scanner per la lingua, come descritto in [parser e scanner del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     La modalità di implementazione del parser e dello scanner è interamente all'utente e esula dall'ambito di questo argomento.

## <a name="language-service-features"></a>Funzionalità del servizio di linguaggio
 Per implementare ogni funzionalità nel servizio di linguaggio, è in genere necessario derivare una classe dalla classe del servizio di linguaggio MPF appropriata, implementare tutti i metodi astratti in base alle esigenze ed eseguire l'override dei metodi appropriati. Le classi create e/o derivate da dipendono dalle funzionalità che si intende supportare. Queste funzionalità sono descritte in dettaglio nelle [funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md). La procedura seguente è l'approccio generale per la derivazione di una classe dalle classi MPF.

#### <a name="deriving-from-an-mpf-class"></a>Derivazione da una classe MPF

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto VSPackage e scegliere **Aggiungi**, **classe**.

2. Assicurarsi che la **classe** sia selezionata nell'elenco modelli.

     Immettere un nome appropriato per il file di classe e fare clic su **Aggiungi**.

3. Nel nuovo file di classe aggiungere le `using` direttive seguenti.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modificare la classe in modo che derivi dalla classe MPF desiderata.

5. Aggiungere un costruttore di classe che accetta almeno gli stessi parametri del costruttore della classe di base e passare i parametri del costruttore al costruttore della classe base.

     Ad esempio, il costruttore per una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Source> classe potrebbe essere simile al seguente:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Dal menu **modifica**, **IntelliSense** , selezionare **implementa classe astratta** se la classe base dispone di metodi astratti che devono essere implementati.

7. In caso contrario, posizionare il punto di inserimento all'interno della classe e immettere il metodo di cui eseguire l'override.

     Digitare, ad esempio, `public override` per visualizzare un elenco di tutti i metodi di cui è possibile eseguire l'override in tale classe.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
