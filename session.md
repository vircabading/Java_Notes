# How to use Session

## Implementing
```
@Controller
public class MainController {
    public String index(HttpSession session){
        // Here we can use the variable session to store things!
        return "index.html"
    }
```
-------------------------------------------

## Setting Session:
```
session.setAttribute("count", 0);
```

-------------------------------------------

## Getting Session:
```
public String showCount(HttpSession session, Model model) {
    Integer currentCount = (Integer) session.getAttribute("count");
    model.addAttribute("countToShow", currentCount);
    return "showCount.jsp";
}
```

--------------------------------------------

## Updating Session:
```
session.setAttribute("count", 0);
```