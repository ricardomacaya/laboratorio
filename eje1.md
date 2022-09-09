use std::io::stdin;
// esta funcion separa los digitos y multiplica cada uno con su correspondiente
// par y luego los resultados se suman, posterior a esto se hace el "mut 11"
// arrogando si es igual a cero true y si es distinto de cero false
fn is_isbn10(clean_isbn: &str) -> bool{
    let mut valor = 0;
    let mut cont = 0;
    let mut c = 0;
    for e in clean_isbn.bytes(){
        cont = 10;
        c = e * cont;
        valor = valor + c;
        cont = cont - 1;
        if cont == 0{
            if valor%11 == 0{
                let x = true;
            }else{
                let x = false;
            }
            }
        }
        return x
}


fn is_isbn_format_valid(c: &str) -> bool {

    // esta funcion valida datos numercios y "x" ya que corersponde a 10
    if c.chars().next().unwrap().is_numeric() {
        return true;
    } else if c == "X" || c == "x"{
        return true;
    }
    return false
}

fn main(){
//crea variables 
    let mut isbn: String = String::new();
    let mut clean_isbn: String = String::new();
    stdin().read_line(&mut isbn).unwrap();
   
    //este ciclo lo que hace es sumar los respectivos valores 
    //que estan siendo ingresados por "is_isbn_format_valid"
    for c in isbn.to_string().trim().chars(){
        if is_isbn_format_valid(&c.to_string()){
            clean_isbn = clean_isbn + &c.to_string(); 
        }
    }
    println!("{}", clean_isbn);
    // recibe el valor true or false con el fin de distinguir
    // el resultado y imprimirlo en la pantalla
    if is_isbn10(&clean_isbn){
        println!("{} es un ISBN10 valido", clean_isbn);
    } else {
        println!("No lo es");
    }

}
