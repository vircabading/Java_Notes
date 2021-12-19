# JSP SNIPPETS

## Form:Form Table
```
<form:form action="/expenses" method="post" modelAttribute="expense">

</form:form>
```

------------------------------------

## Form:Input Name
```
<p class="form-group">
    <form:label path="title">Book Title:</form:label>
    <strong>
        <form:errors path="title" class="alert text-danger" />
    </strong>
    <form:input class="form-control mb-3" path="title" />
</p>
```

-------------------------------------

## Form:Input Currency
```
<p class="form-group">
    <form:label path="amount">Amount in $</form:label>
    <form:input class="form-control mb-3" type="number" path="amount"
        step="0.01" />
    <form:errors path="amount" class="alert alert-danger" />
</p>
```

-------------------------------------
## Form:Input Date
```
<p>
    <form:label path="dueDate">Due Date:</form:label>
    <strong> <form:errors path="dueDate"
            class="alert text-danger" />
    </strong>
    <form:input class="form-control mb-3" type="date" path="dueDate" />
</p>
```

-------------------------------------

## Form:TextArea
```
<p class="form-group">
    <form:label path="description">Description</form:label>
    <form:textarea class="form-control mb-3" path="description" />
    <form:errors path="description" class="alert alert-danger mb-3" />
</p>
```

-------------------------------------

## Form:Button
```
<input class="btn btn-success mb-3" type="submit" value="Submit" />
```

-------------------------------------

## PUT: Convert Post Mapping into PUT Mapping
```
<input type="hidden" name="_method" value="put">	<!-- ### Converts method of form to PUT ### -->
```

-------------------------------------

## Insert a Hidden: user_id used in joining tables
```
<!-- **** User Id **** -->
<form:hidden path="user" value="${user_id}" />
```

=====================================================

# Set Up Get All Table
```
<table class="table table-dark">
    <thead>
        <tr>
            <th scope="col"></th>
        </tr>
    </thead>
    <tbody>
        <c:forEach var="expense" items="${ expenses }">
            <tr>
                <td>${  }</td>
            </tr>
        </c:forEach>
    </tbody>
</table>
```

---------------------------------------------------

## Table Column with link
```
<td><a href="/expenses/${ expense.id }">${ expense.name }</a></td>
```

----------------------------------------------------

## Table Column Currency
```
<td>
    <fmt:formatNumber value="${expense.amount}"
                        type="currency" />
</td>
```

----------------------------------------------------

## Table Column Date
```
<td><fmt:formatDate value="${ eachProject.dueDate }" type="date"></td>
```

----------------------------------------------------

## Table Column Action Buttons
```
<td class="row">
    <!-- **** Button that points to View ************ -->
    <div class="col">
    <button class="col btn btn-primary btn-sm round" 
        onclick="window.location.href='/books/${ eachBook.id }';">View</button>
    </div>
    <!-- **** Button that points to Edit ************ -->
    <form class="col"
        action="/books/${ eachBook.id }/edt" method="post">
        <!-- ### Converts method of form to PUT ### -->
        <input type="hidden" name="_method" value="put">
        <button class="btn btn-warning btn-sm round">Edit</button>
    </form>

    <button class="col btn btn-warning btn-sm round" 
        onclick="window.location.href='/books/${ eachBook.id }/edit';">Edit</button>
    </div>
    <!-- **** Button that Deletes ************ -->
    <form class="col"
        action="/books/${ eachBook.id }/delete" method="post">
        <input type="hidden" name="_method" value="delete">
        <!-- ### Converts method of form to DELETE ### -->
        <button class="btn btn-danger btn-sm round">Delete</button>
    </form>
</td>
```

