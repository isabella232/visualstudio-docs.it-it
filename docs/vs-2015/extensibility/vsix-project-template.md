---
title: Modello di progetto VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2386f1be805f6347fc32fba4ee8bfe57c8602329
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840079"
---
# <a name="vsix-project-template"></a>Modello di progetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare il modello di progetto VSIX per eseguire il wrapping di una o più estensioni di Visual Studio in un progetto VSIX e quindi pubblicare il pacchetto nel sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .  
  
 La distribuzione VSIX supporta VSPackage, assembly, componenti MEF, modelli di progetto, modelli di elemento, controlli della casella degli strumenti e tipi di estensione personalizzati.  
  
> [!NOTE]
> Per usare i progetti VSIX, è necessario installare Visual Studio SDK. Per ulteriori informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Dove trovare il modello di progetto VSIX  
 Il modello di progetto VSIX è disponibile nella finestra di dialogo **nuovo progetto** . Espandere il nodo **Visual Basic** o il nodo **Visual C#** , quindi scegliere **Extensibility**.  
  
> [!TIP]
> Verificare che nell'elenco a discesa nella parte superiore della finestra di dialogo **nuovo progetto** sia specificato .NET Framework 4,5 o versione successiva.  
  
## <a name="uses-of-the-vsix-project-template"></a>Usi del modello di progetto VSIX  
 Il modello di progetto VSIX ha due usi principali:  
  
- Per distribuire modelli di progetto, modelli di elemento e altre estensioni che non hanno ancora il supporto VSIX.  
  
- Per eseguire il wrapping degli output di più estensioni in un unico pacchetto di distribuzione.  
  
  Non è necessario usare il modello di progetto VSIX per distribuire pacchetti VSPackage o altri tipi di estensioni che hanno già il supporto VSIX.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Creazione del pacchetto di un'estensione in un progetto VSIX vuoto  
 È possibile creare un pacchetto di un'estensione esistente o di un'estensione che non ha ancora il supporto VSIX, eseguendone il wrapping in un progetto VSIX vuoto. L'estensione da incapsulare deve essere di un tipo supportato dallo [schema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Per creare un pacchetto di un'estensione usando un progetto VSIX  
  
1. Compilare i progetti che compongono l'estensione.  
  
2. Creare un progetto VSIX usando il modello di **progetto VSIX** .  
  
     Source. Extension. vsixmanifest viene aperto in **Progettazione manifesto**.  
  
3. Nella scheda **Asset** scegliere il pulsante **nuovo** .  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .  
  
4. Nell'elenco **tipo** scegliere il tipo di estensione da aggiungere.  
  
5. Per aggiungere un'estensione o un elemento di contenuto incluso nella soluzione corrente (ad esempio, un modello di elemento o un assembly compilato), seguire questa procedura:  
  
    1. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.  
  
    2. Nell'elenco **progetto** scegliere il nome dell'estensione.  
  
    3. Nella casella **incorpora in questa cartella** immettere il nome di una cartella in cui incorporare l'asset, quindi scegliere il pulsante **OK** .  
  
6. Per aggiungere un'estensione o un elemento di contenuto che non è incluso nella soluzione corrente, seguire questa procedura:  
  
    1. Nella casella di riepilogo **origine** scegliere **file su file System**.  
  
    2. Nel campo **percorso** immettere il percorso completo del file di estensione compilato o compresso oppure usare il pulsante **Sfoglia** per selezionare il file.  
  
    3. Nella casella **incorpora in questa cartella** immettere il nome di una cartella in cui incorporare l'asset, quindi scegliere il pulsante **OK** .  
  
7. Se si desidera che il pacchetto includa estensioni aggiuntive, aggiungerle nello stesso modo.  
  
8. Compilare la soluzione.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Compila un file con estensione VSIX contenente un file manifesto VSIX, un file [Content_Types]. XML e tutte le risorse di estensione aggiunte al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di estensione VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
