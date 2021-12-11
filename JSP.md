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
    <form:label path="name">Expense name:</form:label>
    <form:input class="form-control mb-3" path="name" />
    <form:errors path="name" class="alert alert-danger mb-3" />
</p>
```

-------------------------------------

## Form:Input Currency
```
<p class="form-group">
    <form:label path="amount">Amount in $</form:label>
    <form:input class="form-control mb-3" type="number" path="amount"
        min="0.01" step="0.01" />
    <form:errors path="amount" class="alert alert-danger" />
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