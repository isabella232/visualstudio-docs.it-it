---
title: Modello di progetto VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2b06582e1de7939e34f8fa49aa1cc9435010789
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733855"
---
# <a name="vsix-project-template"></a>Modello di progetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare il modello di progetto VSIX per eseguire il wrapping di uno o più estensioni di Visual Studio in un progetto VSIX e quindi pubblicare il pacchetto nel [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web.  
  
 Distribuzione VSIX supporta i pacchetti VSPackage, assembly, MEF componenti, i modelli di progetto, i modelli di elemento, i controlli della casella degli strumenti e tipi di estensione personalizzati.  
  
> [!NOTE]
>  Per usare progetti VSIX, è necessario installare Visual Studio SDK. Per altre informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Dove trovare il modello di progetto VSIX  
 Il modello di progetto VSIX è disponibile nel **nuovo progetto** nella finestra di dialogo. Espandere la **Visual Basic** nodo o il **Visual c#** nodo e quindi scegliere **estendibilità**.  
  
> [!TIP]
>  È necessario assicurarsi che .NET Framework 4.5 o versione successiva è specificato nell'elenco a discesa nella parte superiore del **nuovo progetto** nella finestra di dialogo.  
  
## <a name="uses-of-the-vsix-project-template"></a>Utilizzi del modello di progetto VSIX  
 Il modello di progetto VSIX ha due utilizzi principali:  
  
- Per distribuire i modelli di progetto, modelli di elementi e altre estensioni che non dispongono ancora il supporto VSIX.  
  
- Per eseguire il wrapping gli output di più estensioni nel pacchetto una distribuzione.  
  
  Non è necessario usare il modello di progetto VSIX per distribuire i pacchetti VSPackage o altri tipi di estensioni che hanno già VSIX supporto.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Creazione del pacchetto di un'estensione in un progetto VSIX vuota  
 È possibile creare un pacchetto, un'estensione esistente o un'estensione che non dispone già di VSIX supportare, inserendoli in un progetto VSIX vuoto. L'estensione da sottoporre a wrapping deve essere di un tipo supportato dal [schema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Per creare un pacchetto di un'estensione usando un progetto VSIX  
  
1.  Compilare i progetti che costituiscono l'estensione.  
  
2.  Creare un progetto VSIX usando il **progetto VSIX** modello.  
  
     Consente di aprire vsixmanifest nel **progettazione manifesto**.  
  
3.  Nel **asset** scheda, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
4.  Nel **tipo** elenco, scegliere il tipo di estensione da aggiungere.  
  
5.  Per aggiungere un elemento di estensione o contenuto che è incluso nella soluzione corrente (ad esempio, un modello di elemento o un assembly compilato), seguire i passaggi seguenti:  
  
    1.  Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.  
  
    2.  Nel **progetto** scegliere il nome dell'estensione.  
  
    3.  Nel **incorpora in questa cartella** immettere il nome di una cartella in cui si desidera incorporare l'asset e quindi scegliere il **OK** pulsante.  
  
6.  Per aggiungere un elemento di contenuto che non è incluso nella soluzione corrente o un'estensione, seguire i passaggi seguenti:  
  
    1.  Nel **origine** elenco a discesa, scegliere **File in filesystem**.  
  
    2.  Nel **percorso** campo, immettere il percorso completo al file di estensione compilato o compresso o utilizzare il **Sfoglia** pulsante per individuare il file.  
  
    3.  Nel **incorpora in questa cartella** immettere il nome di una cartella in cui si desidera incorporare l'asset e quindi scegliere il **OK** pulsante.  
  
7.  Se si desidera che il pacchetto a includere le estensioni aggiuntive, aggiungerle allo stesso modo.  
  
8.  Compilare la soluzione.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Compila un file con estensione VSIX che contiene un file manifesto VSIX, un file [Content_Types] XML e tutte le risorse di estensione che è stato aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti su VSIX Extension Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)

