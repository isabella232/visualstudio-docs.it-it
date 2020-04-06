---
title: Esporre elenchi di simboli forniti a Gestione oggetti . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsSimpleLibrary2 interface, lists of symbols
- IVsLibrary2 interface, lists of symbols
- symbols, call browser
- lists, symbols for the object manager
- symbols, exposing lists to the object manager
ms.assetid: 19757068-bdaa-4e7e-85d6-f8ce5026a859
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb15b7d9b29c578a0acf43fd1aa9cfdea88e23ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708079"
---
# <a name="how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager"></a>Procedura: esporre all'object manager elenchi di simboli forniti dalla libreria
Gli strumenti di esplorazione dei simboli, Visualizzazione classi , **Visualizzatore** **oggetti**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Visualizzatore chiamate** e Risultati ricerca **simbolo**, passano le richieste di nuovi dati al gestore oggetti. Il gestore di oggetti trova le librerie appropriate e richiede nuovi elenchi di simboli. Le librerie rispondono fornendo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i dati <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> richiesti al gestore di oggetti tramite l'interfaccia. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> oggetti chiama i metodi in interfaccia per ottenere i dati e li utilizza per popolare o aggiornare le visualizzazioni degli strumenti di esplorazione dei simboli.

 Una libreria può ottenere richieste di dati quando lo strumento viene richiamato, il nodo viene espanso o la visualizzazione viene aggiornata. Quando uno strumento di esplorazione dei simboli viene richiamato per la prima volta, il gestore di oggetti richiede alla libreria di fornire l'elenco di primo livello. Quando l'utente espande un nodo di elenco, la libreria fornisce un elenco di elementi figlio in tale nodo. Ogni richiesta di richiesta di gestione oggetti contiene un indice dell'elemento di interesse. Per visualizzare un nuovo elenco, il gestore di oggetti deve determinare il numero di elementi presenti nell'elenco, il tipo di elementi, i relativi nomi, l'accessibilità e altre proprietà.

> [!NOTE]
> Negli esempi di codice gestito seguenti viene illustrato <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> come fornire elenchi di simboli tramite l'implementazione dell'interfaccia. Il gestore di oggetti chiama i metodi in questa interfaccia e utilizza i dati ottenuti per popolare o aggiornare gli strumenti di esplorazione dei simboli.
>
> Per l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> provider di simboli di codice nativo, usare l'interfaccia .

## <a name="to-provide-lists-of-symbols-to-the-object-manager"></a>Per fornire elenchi di simboli al gestore oggetti

1. Ottenere il numero di elementi nell'elenco <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> di simboli implementando il metodo . Nell'esempio seguente viene illustrato come il gestore di oggetti ottiene le informazioni sul numero di elementi nell'elenco.

    ```vb
    Protected m_Methods As System.Collections.Generic.SortedList(Of String, Method) = New System.Collections.Generic.SortedList(Of String, Method)()

    Public Function GetItemCount(ByRef pCount As UInteger) As Integer
        pCount = CUInt(m_Methods.Count)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    protected System.Collections.Generic.SortedList<string, Method> m_Methods = new System.Collections.Generic.SortedList<string, Method>();

    public int GetItemCount(out uint pCount)
    {
        pCount = (uint)m_Methods.Count;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

2. Ottenere informazioni sulle categorie e gli attributi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> un determinato elemento dell'elenco implementando il metodo . Le categorie di elementi <xref:Microsoft.VisualStudio.Shell.Interop.LIB_CATEGORY> vengono specificate nell'enumerazione. Nell'esempio seguente viene illustrato come il gestore di oggetti ottiene gli attributi degli elementi per una determinata categoria.

    ```vb
    Public Function GetCategoryField2(ByVal index As UInteger, ByVal Category As Integer, ByRef pfCatField As UInteger) As Integer
        pfCatField = 0

        Select Case CType(Category, LIB_CATEGORY)
            Case LIB_CATEGORY.LC_MEMBERTYPE
                pfCatField = CUInt(_LIBCAT_MEMBERTYPE.LCMT_METHOD)

            Case LIB_CATEGORY.LC_MEMBERACCESS
                Dim method As Method = m_Methods.Values(CInt(Fix(index)))

                If method.IsPublic Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PUBLIC)
                ElseIf method.IsPrivate Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PRIVATE)
                ElseIf method.IsFamily Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED)
                ElseIf method.IsFamilyOrAssembly Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED) Or CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)
                Else
                    ' Show everything else as internal.
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)
                End If

            Case LIB_CATEGORY.LC_VISIBILITY
                pfCatField = CUInt(_LIBCAT_VISIBILITY.LCV_VISIBLE)

            Case LIB_CATEGORY.LC_LISTTYPE
                pfCatField = CUInt(_LIB_LISTTYPE.LLT_MEMBERS)

            Case Else
                Return Microsoft.VisualStudio.VSConstants.S_FALSE
        End Select
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int GetCategoryField2(uint index, int Category, out uint pfCatField)
    {
        pfCatField = 0;

        switch ((LIB_CATEGORY)Category)
        {
            case LIB_CATEGORY.LC_MEMBERTYPE:
                pfCatField = (uint)_LIBCAT_MEMBERTYPE.LCMT_METHOD;
                break;

            case LIB_CATEGORY.LC_MEMBERACCESS:
                {
                    Method method = m_Methods.Values[(int)index];

                    if (method.IsPublic)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PUBLIC;
                    }
                    else if (method.IsPrivate)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PRIVATE;
                    }
                    else if (method.IsFamily)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED;
                    }
                    else if (method.IsFamilyOrAssembly)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED |
                                     (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;
                    }
                    else
                    {
                        // Show everything else as internal.
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;
                    }
                }
                break;

            case LIB_CATEGORY.LC_VISIBILITY:
                pfCatField = (uint)_LIBCAT_VISIBILITY.LCV_VISIBLE;
                break;

            case LIB_CATEGORY.LC_LISTTYPE:
                pfCatField = (uint)_LIB_LISTTYPE.LLT_MEMBERS;
                break;

            default:
                return Microsoft.VisualStudio.VSConstants.S_FALSE;
        }
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

3. Ottenere la rappresentazione testuale <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> di un determinato elemento dell'elenco implementando il metodo. Nell'esempio seguente viene illustrato come ottenere un nome completo di un determinato elemento.

    ```vb
    Public Function GetTextWithOwnership(<System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")> ByVal index As UInteger, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")> ByVal tto As Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")> ByRef ppszText As String) As Integer
        ppszText = m_Methods.Values(CInt(Fix(index))).FullName
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int GetTextWithOwnership([System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")] uint index, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")] Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS tto, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")] out string ppszText)
    {
        ppszText = m_Methods.Values[(int)index].FullName;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

4. Ottenere le informazioni sull'icona per un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> determinato elemento dell'elenco implementando il metodo. L'icona rappresenta il tipo (classe, metodo e così via) e l'accessibilità (privata, pubblica e così via) di una voce di elenco. Nell'esempio seguente viene illustrato come ottenere le informazioni sull'icona in base agli attributi di un elemento specificato.

    ```vb
    Public Overridable Function GetDisplayData(ByVal index As UInteger, ByVal pData As Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA()) As Integer
        If pData Is Nothing Then
            Return Microsoft.VisualStudio.VSConstants.E_INVALIDARG
        End If

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))

        Dim iImage As Integer = 12 * 6 ' See env\inc\OMGlyphs.h.

        Const OM_GLYPH_ACC_PUBLIC As Integer = 0
        Const OM_GLYPH_ACC_INTERNAL As Integer = 1
        Const OM_GLYPH_ACC_PROTECTED As Integer = 3
        Const OM_GLYPH_ACC_PRIVATE As Integer = 4

        If method.IsPublic Then
            iImage += OM_GLYPH_ACC_PUBLIC
        ElseIf method.IsPrivate Then
            iImage += OM_GLYPH_ACC_PRIVATE
        ElseIf method.IsFamily Then
            iImage += OM_GLYPH_ACC_PROTECTED
        ElseIf method.IsFamilyOrAssembly Then
            iImage += OM_GLYPH_ACC_PROTECTED
        Else
            iImage += OM_GLYPH_ACC_INTERNAL
        End If

        pData(0).Image = CUShort(iImage)
        pData(0).SelectedImage = CUShort(iImage)

        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public virtual int GetDisplayData(uint index, Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA[] pData)
    {
        if (pData == null)
        {
            return Microsoft.VisualStudio.VSConstants.E_INVALIDARG;
        }

        Method method = m_Methods.Values[(int)index];

        int iImage = 12 * 6;    // See env\inc\OMGlyphs.h.

        const int OM_GLYPH_ACC_PUBLIC = 0;
        const int OM_GLYPH_ACC_INTERNAL = 1;
        const int OM_GLYPH_ACC_PROTECTED = 3;
        const int OM_GLYPH_ACC_PRIVATE = 4;

        if (method.IsPublic)
        {
            iImage += OM_GLYPH_ACC_PUBLIC;
        }
        else if (method.IsPrivate)
        {
            iImage += OM_GLYPH_ACC_PRIVATE;
        }
        else if (method.IsFamily)
        {
            iImage += OM_GLYPH_ACC_PROTECTED;
        }
        else if (method.IsFamilyOrAssembly)
        {
            iImage += OM_GLYPH_ACC_PROTECTED;
        }
        else
        {
            iImage += OM_GLYPH_ACC_INTERNAL;
        }

        pData[0].Image = (ushort)iImage;
        pData[0].SelectedImage = (ushort)iImage;

        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

5. Ottenere le informazioni su se un determinato elemento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> dell'elenco è espandibile implementando il metodo. Nell'esempio seguente viene illustrato come ottenere le informazioni su se un determinato elemento può essere espanso.

    ```vb
    Public Function GetExpandable(ByVal index As UInteger, ByRef pfExpandable As Integer) As Integer
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    Public Function GetExpandable3(ByVal index As UInteger, ByVal ListTypeExcluded As UInteger, ByRef pfExpandable As Integer) As Integer
        Return GetExpandable(index, pfExpandable)
    End Function
    ```

    ```csharp
    public int GetExpandable(uint index, out int pfExpandable)
    {
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    public int GetExpandable3(uint index, uint ListTypeExcluded, out int pfExpandable)
    {
        return GetExpandable(index, out pfExpandable);
    }

    ```

6. Ottenere un elenco figlio di simboli di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> un determinato elemento dell'elenco implementando il metodo. Nell'esempio seguente viene illustrato come ottenere un elenco figlio di simboli di un determinato elemento per i grafici **Call** o **Callers.**

    ```vb
    ' Call graph list.
    Public Class CallsList
        Inherits ResultsList
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
        Public Sub New(ByVal library As Library)
            MyBase.New(library)
        End Sub

        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
            Return MyBase.GetCallsList(index, ppList)
        End Function
    End Class

    ' Callers graph list.
    Public Class CallersList
        Inherits ResultsList
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
        Public Sub New(ByVal library As Library)
            MyBase.New(library)
        End Sub

        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
            Return MyBase.GetCallersList(index, ppList)
        End Function
    End Class

    ' Call graph list.
    Public Function GetCallsList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing
        Dim callsList As ResultsList = New CallsList(m_Library)

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        Dim Calls As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallGraph(method)

        For i As Integer = 0 To Calls.Count - 1
            Dim caller As Method = Calls(i).m_Target
            callsList.AddMethod(caller)
        Next i

        ppList = CType(callsList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    ' Callers graph list.
    Public Function GetCallersList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing
        Dim callersList As ResultsList = New CallersList(m_Library)

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        Dim Callers As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallersGraph(method)

        For i As Integer = 0 To Callers.Count - 1
            Dim caller As Method = Callers(i).m_Source
            callersList.AddMethod(caller)
        Next i

        ppList = CType(callersList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    ' Get a child list of symbols for a given list item.
    Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        ' Determine if the list belongs to Call or Callers graphs.
        If CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM)) > 0 Then
            ' Build the list for the Call graph.
            Return MyBase.GetCallsList(index, ppList)
        ElseIf CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO)) > 0 Then
            ' Build the list for the Callers graph.
            Return MyBase.GetCallersList(index, ppList)
        End If

        Return Microsoft.VisualStudio.VSConstants.E_FAIL
    End Function
    ```

    ```csharp
    // Call graph list.
    public class CallsList :
        ResultsList,
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
    {
        public CallsList(Library library) :
            base(library)
        {
        }

        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
        {
            return base.GetCallsList(index, out ppList);
        }
    }

    // Callers graph list.
    public class CallersList :
        ResultsList,
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
    {
        public CallersList(Library library) :
            base(library)
        {
        }

        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
        {
            return base.GetCallersList(index, out ppList);
        }
    }

    // Call graph list.
    public int GetCallsList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;
        ResultsList callsList = new CallsList(m_Library);

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        System.Collections.Generic.List<CallInstance> Calls = m_Library.CallGraph.GetCallGraph(method);

        for (int i = 0; i < Calls.Count; i++)
        {
            Method caller = Calls[i].m_Target;
            callsList.AddMethod(caller);
        }

        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callsList);
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    // Callers graph list.
    public int GetCallersList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;
        ResultsList callersList = new CallersList(m_Library);

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        System.Collections.Generic.List<CallInstance> Callers = m_Library.CallGraph.GetCallersGraph(method);

        for (int i = 0; i < Callers.Count; i++)
        {
            Method caller = Callers[i].m_Source;
            callersList.AddMethod(caller);
        }

        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callersList);
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    // Get a child list of symbols for a given list item.
    public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        // Determine if the list belongs to Call or Callers graphs.
        if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM) > 0)
        {
            // Build the list for the Call graph.
            return base.GetCallsList(index, out ppList);
        }
        else if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO) > 0)
        {
            // Build the list for the Callers graph.
            return base.GetCallersList(index, out ppList);
        }

        return Microsoft.VisualStudio.VSConstants.E_FAIL;
    }

    ```

## <a name="see-also"></a>Vedere anche
- [Supporta gli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Procedura: registrare una libreria con il gestore di oggettiHow to: Register a library with the object manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Procedura: identificare i simboli in una libreriaHow to: Identify symbols in a library](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
- [Estendibilità del servizio di linguaggio legacyLegacy language service extensibility](../../extensibility/internals/legacy-language-service-extensibility.md)
