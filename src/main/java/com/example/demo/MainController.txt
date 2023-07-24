package com.example.demo;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
@RequestMapping(path="/")
public class MainController {
     @Autowired
    private InstrumentoRepository repository;

    @Autowired
    private JdbcTemplate jdbcTemplate;

   @GetMapping(path="/api/ec3/instrumento/listar")
    public @ResponseBody Iterable<Instrumento> listar(){
        return repository.findAll();
    }
    @PostMapping(path = "/api/ec3/instrumento/nuevo")
    public @ResponseBody String addNewInstrumento(
        @RequestParam String nombre)
    {
        Instrumento n =new Instrumento();
        n.setNombre(nombre);
        repository.save(n);
        return "Instrumento Guardado";
    }
 
}
