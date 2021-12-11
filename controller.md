# Controller Snippets

## Create
```
@PostMapping("/dojos/new")
public String dojosNewPost(@Valid @ModelAttribute("dojo") Dojo dojo,
            BindingResult result, Model model) {
    if (result.hasErrors()) {
        List<Dojo> dojosList = this.dojoServ.retrieveAll();
        model.addAttribute("dojosList",dojosList);
        return "dojosnew.jsp";
    } else {
        this.dojoServ.create(dojo);
        return "redirect:/dojos";
    }
}
```