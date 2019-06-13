---
title: Finestra di dialogo Informazioni assembly
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c5420839d97fb62797d0f739ce62da4d14b340b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744889"
---
# <a name="assembly-information-dialog-box"></a>Finestra di dialogo Informazioni assembly
Il **informazioni sull'Assembly** nella finestra di dialogo consente di specificare i valori degli attributi dell'assembly globale di .NET Framework, che vengono archiviati nel file AssemblyInfo creato automaticamente con il progetto. In **Esplora soluzioni** il file è contenuto nel nodo **My Project** (Progetto) in [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. Fare clic su **Mostra tutti i file** per visualizzarlo. Si trova in **Proprietà** in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Per altre informazioni sugli attributi degli assembly, vedere [Attributi](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, fare clic su **Proprietà** dal menu **Progetto**. Quando si apre **Creazione progetti**, fare clic sulla scheda **Applicazione**. Nella pagina **Applicazione** scegliere il pulsante **Informazioni assembly**.

## <a name="uielement-list"></a>Elenco UIElement
 **Titolo** Specifica un titolo per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyTitleAttribute>.

 **Descrizione** Specifica una descrizione facoltativa per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyDescriptionAttribute>.

 **Società** Specifica il nome di una società per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyCompanyAttribute>.

 **Prodotto** Specifica il nome di un prodotto per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyProductAttribute>.

 **Copyright** Specifica le informazioni sul copyright per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyCopyrightAttribute>.

 **Marchio** Specifica un marchio per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyTrademarkAttribute>.

 **Versione dell'assembly** Specifica la versione dell'assembly di cui definire l'attributo. Corrisponde a <xref:System.Reflection.AssemblyVersionAttribute>.

 **Versione file**Specifica a un numero di versione che indica al compilare di usare una versione specifica per la risorsa della versione del file Win32. Corrisponde a <xref:System.Reflection.AssemblyFileVersionAttribute>.

 **GUID** Un GUID univoco che identifica l'assembly. Quando si crea un progetto, Visual Studio genera un GUID per l'assembly. Corrisponde a <xref:System.Guid>.

 **Lingua neutra** Specifica le impostazioni cultura supportate dall'assembly. Corrisponde a <xref:System.Resources.NeutralResourcesLanguageAttribute>. L'impostazione predefinita è **(Nessuna)** .

 **Rendi assembly visibile a COM** Specifica se i tipi nell'assembly saranno disponibili a COM. Corrisponde a <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

## <a name="see-also"></a>Vedere anche

- [Pagina Applicazione, Creazione progetti (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Attributi](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)