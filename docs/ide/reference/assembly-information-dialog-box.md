---
title: Finestra di dialogo Informazioni assembly
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1813c4e399a125aca0185436b4a7216b72b5842
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809007"
---
# <a name="assembly-information-dialog-box"></a>Finestra di dialogo Informazioni assembly

È possibile usare la finestra di dialogo Informazioni assembly per specificare i valori degli attributi globali degli assembly di .NET Framework che vengono archiviati nel file AssemblyInfo creato automaticamente insieme al progetto. In Esplora soluzioni il file AssemblyInfo è contenuto nel nodo **Progetto** per i progetti Visual Basic. Fare clic su **Mostra tutti i file** per visualizzarlo. Per i progetti C#, si trova in **Proprietà**. Per altre informazioni, vedere [Attributi (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Per accedere a questa finestra di dialogo, selezionare un nodo del progetto in **Esplora soluzioni** e quindi scegliere **Proprietà** dal menu **Progetto**. Nella pagina **Applicazione** selezionare il pulsante **Informazioni assembly**.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Titolo**\
Specifica un titolo per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyTitleAttribute>.

**Descrizione**\
Specifica una descrizione facoltativa per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyDescriptionAttribute>.

**Azienda**\
Specifica il nome di una società per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyCompanyAttribute>.

È possibile impostare o modificare il valore predefinito per Società nel Registro di sistema. Cercare il valore **RegisteredOrganization** nella chiave **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** o **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion**, a seconda della versione di Windows.

**Prodotto**\
Specifica il nome di un prodotto per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyProductAttribute>.

**Copyright**\
Specifica le informazioni sul copyright per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Marchio**\
Specifica un marchio per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyTrademarkAttribute>.

**Versione assembly**\
Specifica la versione dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyVersionAttribute>.

**Versione file**\
Specifica a un numero di versione che indica al compilare di usare una versione specifica per la risorsa della versione del file Win32. Corrisponde a <xref:System.Reflection.AssemblyFileVersionAttribute>.

**GUID**\
Un GUID univoco che identifica l'assempbly. Quando si crea un progetto, Visual Studio genera un GUID per l'assembly. Corrisponde a <xref:System.Guid>.

**Lingua neutra**\
Specifica le impostazioni cultura supportate dall'assembly. Corrisponde a <xref:System.Resources.NeutralResourcesLanguageAttribute>. Il valore predefinito è **(nessuno)**.

**Rendi assembly visibile a COM**\
Specifica se i tipi nell'assembly saranno disponibili a COM. Corrisponde a <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Per altre informazioni sull'impostazione di queste proprietà durante la generazione di un pacchetto NuGet in una libreria di classi .NET Framework, vedere [configurare le proprietà del progetto per il pacchetto](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Vedere anche

- [Application Page, Project Designer (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Attributes (Attributi)](/previous-versions/z0w1kczw(v=vs.140))