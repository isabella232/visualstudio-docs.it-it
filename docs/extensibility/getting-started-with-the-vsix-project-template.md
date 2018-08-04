---
title: Introduzione al modello di progetto VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28aa6c6e2b7aca671b1f1ac9d9be7f34261b867b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499439"
---
# <a name="get-started-with-the-vsix-project-template"></a>Iniziare con il modello di progetto VSIX
È possibile usare il modello di progetto VSIX per creare un'estensione o per un'estensione esistente per la distribuzione del pacchetto. Il modello di progetto VSIX contiene le versioni di Visual Basic e Visual c# e viene installato come parte di Visual Studio SDK.  
  
 Il modello di progetto VSIX è costituito semplicemente una *vsixmanifest* file che contiene informazioni sull'estensione e gli asset è disponibile.  
  
 Per trovare il modello di progetto VSIX, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Distribuire un modello di progetto personalizzati usando il modello di progetto VSIX  
 I passaggi seguenti illustrano come usare il progetto VSIX per creare un pacchetto di un modello di progetto che è possibile condividere con altri sviluppatori o caricare in Visual Studio Gallery.  
  
1.  Creare un modello di progetto.  
  
    1.  Aprire il progetto da cui creare un modello. Questo progetto può essere di qualsiasi tipo di progetto.  
  
    2.  Nel menu **Progetto** scegliere**Esporta modello**. Completare i passaggi della procedura guidata.  
  
         Oggetto *zip* file viene creato nella *%USERPROFILE%\My Documents\Visual Studio \<versione > \My Exported Templates\\*.  
  
2.  Creare un progetto VSIX vuoto.  
  
     Scegliere **Nuovo** dal menu **File** , quindi fare clic su **Progetto**. Selezionare uno **Visual Basic** oppure **Visual c#**. Sotto il nodo selezionato, selezionare **estendibilità**, quindi selezionare **progetto VSIX**.  
  
3.  Aggiungere il *zip* file al progetto. Impostare relativi **copia in Directory di Output** proprietà `Copy Always`.  
  
4.  Nel **Esplora soluzioni**, fare doppio clic il *vsixmanifest* file per aprirlo nel **progettazione del manifesto VSIX**e quindi apportare le modifiche seguenti:  
  
    -   Impostare il **Product Name** campo **risorse del modello di progetto**.  
  
    -   Impostare il **ID prodotto** campo **MyProjectTemplate - 1**.  
  
    -   Impostare il **Author** campo **Fabrikam**.  
  
    -   Impostare il **descrizione** campo **modello di progetto personale**.  
  
    -   Nel **asset** sezione, aggiungere un **Microsoft.VisualStudio.ProjectTemplate** digitare e impostarne il percorso al nome del *zip* file.  
  
5.  Salvare e chiudere il *vsixmanifest* file.  
  
6.  Compilare il progetto.  
  
7.  Nella directory di output, fare doppio clic il *VSIX* file.  
  
8.  Oggetto **programma di installazione VSIX** verrà visualizzata la finestra di messaggio. Seguire le istruzioni per installare l'estensione.  
  
9. Chiudere Visual Studio e quindi aprirlo nuovamente.  
  
10. Selezionare **estensioni e aggiornamenti** (nel **Tools** menu) e selezionare il **modelli** categoria. Deve essere una delle estensioni disponibili **modello di progetto personale**.  
  
11. Il nuovo modello di progetto viene visualizzato nei **nuovo progetto** finestra di dialogo nella stessa posizione come il modello di progetto originale. Ad esempio, se è stato creato un modello denominato **VB Console** da un'applicazione console Visual Basic, **Console di Visual Basic** viene visualizzato nel riquadro stesso come Visual Basic **applicazione Console**modello.  
  
### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Per specificare il percorso del modello nella finestra di dialogo Nuovo progetto  
  
1.  Cartelle dei modelli si trovano nel *\Common7\IDE\ProjectTemplates {percorso Visual Studio installazione}* e * \Common7\IDE\ItemTemplates {percorso Visual Studio installazione}} le directory. I nomi di alto livello sezioni nel **nuovo progetto** finestra di dialogo non corrispondono esattamente i nomi delle cartelle dei modelli. Dove si differenziano, usare il nome della cartella del modello.  
  
     Modifica il *VSIX* estensione di file *zip*e quindi aprire il file.  
  
2.  Creare una nuova cartella con lo stesso nome della sezione del **nuovo progetto** il modello deve essere visualizzato nella finestra di dialogo.  
  
3.  Se il modello deve trovarsi in una sottosezione, creare una sottocartella con lo stesso nome.  
  
4.  Spostare il modello *zip* file nella nuova cartella.  
  
5.  Modifica il *zip* estensione *VSIX*.  
  
6.  Aprire il manifesto VSIX.  
  
7.  Nel manifesto VSIX, aggiornare il **Asset** percorso del modello in modo che punti alla radice della struttura di directory che contiene il file di modello. Ad esempio, se il modello si trova in *\CSharp\Windows*, il riferimento deve puntare *\CSharp*.