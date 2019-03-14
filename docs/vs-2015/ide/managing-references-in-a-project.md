---
title: Gestione dei riferimenti in un progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 48d6849a6656f5914d11250e26681e208cdb7487
ms.sourcegitcommit: b7f25ae08e45fcaa84a84276b588cf6799cc7620
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57567215"
---
# <a name="managing-references-in-a-project"></a>Gestione dei riferimenti in un progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prima di scrivere codice per un componente esterno o servizio connesso, il progetto deve contenere innanzitutto un riferimento a esso. Un riferimento è essenzialmente una voce in un file di progetto che contiene le informazioni necessarie a Visual Studio per individuare il componente o il servizio.  
  
 Per aggiungere un riferimento, fare clic con il pulsante destro del mouse sul nodo Riferimenti di Esplora soluzioni e scegliere **Aggiungi riferimento**. Per altre informazioni, vedere [Procedura: Aggiungere o rimuovere riferimenti mediante Gestione riferimenti](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  
  
 ![Aggiungere un riferimento in Visual C&#43;&#43;](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")  
  
 È possibile fare riferimento ai seguenti tipi di componenti e servizi:  
  
-   Riferimenti ad app di Windows Store  
  
-   Librerie di classi o assembly .NET Framework  
  
-   componenti COM  
  
-   Altri assembly o librerie di classi dei progetti contenuti nella stessa soluzione  
  
-   servizi Web XML  
  
## <a name="windows-store-app-references"></a>Riferimenti ad app di Windows Store  
  
### <a name="project-references"></a>Riferimenti al progetto  
 I progetti della piattaforma UWP (Universal Windows Platform) destinati a Windows 10 possono creare riferimenti ad altri progetti UWP nella soluzione oppure a progetti o file binari di Windows Store destinati a [!INCLUDE[win81](../includes/win81-md.md)], a condizione che tali progetti non usino API deprecate in Windows 10. Per altre informazioni vedere la pagina relativa al [passaggio da Windows Runtime 8 alla piattaforma UWP](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx).  
  
 Se si sceglie di destinare di nuovo i progetti di [!INCLUDE[win81](../includes/win81-md.md)] per Windows 10, vedere [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)  
  
### <a name="extension-sdk-references"></a>Riferimenti all'SDK di estensione  
 I progetti di Windows Store in Visual Basic, C#, C++ e JavaScript destinati alla piattaforma UWP (Universal Windows Platform) possono fare riferimento a SDK di estensione destinati a [!INCLUDE[win81](../includes/win81-md.md)], a condizione che tali SDK non usino API deprecate in Windows 10. Controllare il sito del fornitore dell'SDK di estensione per verificare se i progetti Windows Store destinati a UWP possono farvi riferimento.  
  
 Se si determina che l'SDK di estensione a cui fa riferimento l'app non è supportato, è necessario eseguire i passaggi seguenti:  
  
1.  Controllare il nome del progetto che causa l'errore. La piattaforma di destinazione del progetto è inserita tra parentesi accanto al nome del progetto. Ad esempio, **NomeProgettoPersonale (Windows 8.1)** significa che il progetto **NomeProgettoPersonale** è destinato alla versione della piattaforma [!INCLUDE[win81](../includes/win81-md.md)].  
  
2.  Andare al sito del fornitore proprietario dell'SDK di estensione non supportato e installare la versione dell'SDK di estensione con dipendenze compatibili con la versione della piattaforma di destinazione del progetto.  
  
    > [!NOTE]
    >  Un modo per verificare se l'SDK di estensione ha dipendenze da altri SDK di estensione, riavviare Visual Studio, creare un nuovo progetto Windows Store in C#, fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi riferimento**, passare alla scheda **Windows** , passare alla sottoscheda **Estensioni** , selezionare l'SDK di estensione e controllare nel riquadro destro di **Gestione riferimenti**. Se dispone di dipendenze, risulteranno elencate.  
  
    > [!IMPORTANT]
    >  Se il progetto è destinato a Windows 10 e l'SDK di estensione installato in precedenza ha una dipendenza da Microsoft Visual C++ Runtime Package, la versione di Microsoft Visual C++ Runtime Package compatibile con Windows 10 è v14.0 e viene installata con Visual Studio 2015.  
  
3.  Se l'SDK di estensione installato in precedenza ha dipendenze da altri SDK di estensione, andare ai siti dei fornitori proprietari delle dipendenze e installare le versioni di queste dipendenze compatibili con la versione della piattaforma di destinazione del progetto.  
  
4.  Riavviare Visual Studio e aprire l'app.  
  
5.  Fare clic con il pulsante destro del mouse sul nodo **Riferimenti** del progetto che ha causato l'errore e scegliere **Aggiungi riferimento**.  
  
6.  Fare clic sulla scheda **Windows** e sulla sottoscheda **Estensioni** , quindi deselezionare le caselle di controllo per l'SDK di estensione precedente e selezionare le caselle di controllo per i nuovi SDK di estensione. Fare clic su **OK**.  
  
## <a name="adding-a-reference-at-design-time"></a>Aggiunta di un riferimento in fase di progettazione  
 Quando si fa riferimento a un assembly nel progetto, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cerca l'assembly nei percorsi seguenti:  
  
-   La directory del progetto corrente. È possibile trovare questi assembly tramite la scheda **Sfoglia** .  
  
-   Altre directory di progetto nella stessa soluzione. È possibile trovare questi assembly tramite la scheda **Progetti** .  
  
> [!NOTE]
>  Tutti i progetti contengono un riferimento implicito a mscorlib. I progetti di Visual Basic contengono un riferimento implicito a `Microsoft.VisualBasic`.  
>   
>  In Visual Studio, tutti i progetti contengono un riferimento implicito a `System.Core`, anche se `System.Core` è rimosso dall'elenco di riferimenti.  
  
## <a name="references-to-shared-components-at-run-time"></a>Riferimenti a componenti condivisi in fase di esecuzione  
 In fase di esecuzione i componenti devono trovarsi nel percorso di output del progetto o nella [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC). Se il progetto contiene un riferimento a un oggetto che non è in uno di questi percorsi, è necessario copiare il riferimento al percorso di output del progetto quando si compila il progetto. La <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> proprietà indica se la copia deve essere eseguita. Se il valore è **True**, il riferimento viene copiato nella directory del progetto quando si compila quest'ultimo. Se il valore è **False**, il riferimento non viene copiato.  
  
 Se si distribuisce un'applicazione che contiene un riferimento a un componente personalizzato registrato nella GAC (Global Assembly Cache), tale componente non verrà distribuito con l'applicazione, indipendentemente dall'impostazione di <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> . Nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]era possibile impostare la proprietà <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> su un riferimento per garantire che l'assembly venisse distribuito. A questo punto, è necessario aggiungere manualmente l'assembly nella cartella \Bin. Con questa operazione è possibile mettere tutto il codice personalizzato sotto controllo, riducendo il rischio di pubblicare codice personalizzato con cui non si ha familiarità.  
  
 Per impostazione predefinita, la proprietà <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> è impostata su **False** se l'assembly o il componente si trova nella Global Assembly Cache o un componente del framework. In caso contrario, il valore è impostato su **True**. I riferimenti da progetto a progetto sono sempre impostati su **True**.  
  
## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Fare riferimento a un progetto o a un componente destinato a una versione differente di .NET Framework.  
 È possibile creare applicazioni che fanno riferimento a progetti o assembly destinati a una versione diversa di .NET Framework. Ad esempio, è possibile creare un'applicazione destinata a [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] che fa riferimento a un assembly destinato a [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)]. Se si crea un progetto destinato a una versione precedente di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], in tale progetto non è possibile impostare un riferimento a un progetto o un assembly destinato a [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] o .NET Framework 4.  
  
 Per altre informazioni, vedere [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="project-to-project-references"></a>Riferimenti da progetto a progetto  
 I riferimenti da progetto a progetto sono riferimenti a progetti che contengono assembly; è possibile crearli tramite la scheda **Progetto** . Visual Studio può trovare un assembly se viene specificato un percorso al progetto.  
  
 In un progetto che produce un assembly, fare riferimento al progetto e non usare un riferimento al file (vedere sotto). Il vantaggio di un riferimento da progetto è che viene creata una dipendenza tra i progetti nel sistema di compilazione. Il progetto dipendente verrà compilato come se fosse stato modificato dall'ultima volta in cui è stato compilato il progetto di riferimento. Un riferimento al file non crea una dipendenza di compilazione, pertanto è possibile compilare il progetto di riferimento senza compilare il progetto dipendente, nel qual caso il riferimento potrebbe diventare obsoleto. Ovvero, il progetto potrebbe fare riferimento a una versione precedente del progetto. Ciò potrebbe comportare l'esigenza di varie versioni di una singola DLL nella directory bin, il che non è possibile. Quando si verifica questo conflitto, viene visualizzato un messaggio simile al seguente: [Avviso: impossibile copiare la dipendenza "file" del progetto "progetto" nella directory di esecuzione perché sovrascriverebbe il riferimento "file"](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied.md). Per altre informazioni, vedere [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md) e [How to: Create and Remove Project Dependencies](../ide/how-to-create-and-remove-project-dependencies.md).  
  
> [!NOTE]
>  Se la versione di destinazione di .NET Framework di un progetto è 4.5 e la versione di destinazione dell'altro progetto è 2, 3, 3.5 o 4.0, viene creato un riferimento al file anziché un riferimento da progetto a progetto.  
  
## <a name="file-references"></a>Riferimenti a file  
 I riferimenti a file sono riferimenti diretti agli assembly esterni al contesto di un progetto di Visual Studio. È possibile crearli usando la scheda **Sfoglia** di **Gestione riferimenti**. Usare un riferimento a file quando si ha solo un assembly o un componente e non il progetto che l'ha creato come output.  
  
## <a name="see-also"></a>Vedere anche  
 [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md)   
 [Programmazione con gli assembly](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [How to: Add or Remove References By Using the Reference Manager](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
