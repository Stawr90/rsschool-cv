1. ## Igor Zharov
2. **EMail** *stawr.900@gmail.com*
3. I am hardworking, assiduous. I am quick to get my head around new material. My goal is to become a professional front-end developer. I have experience in creating simple websites.
4. My skills - *HTML, CSS, Git, JavaScript (Basic level)*
5. **CODE**

```
'use strict';

document.addEventListener('DOMContentLoaded', () => { //когда HTML загружен и обработан, идет считывание js
    const movieDB = {
        movies: [
            "Логан",
            "Лига справедливости",
            "Ла-ла лэнд",
            "Одержимость",
            "Скотт Пилигрим против..."
        ]
    };

    const adv = document.querySelectorAll('.promo__adv img'),
          poster = document.querySelector('.promo__bg'),
          genre = poster.querySelector('.promo__genre'),
          movieList = document.querySelector('.promo__interactive-list'),
          addForm = document.querySelector('form.add'), //доступ ко всей форме
          addInput = addForm.querySelector('.adding__input'), //доступ к форме
          checkbox = addForm.querySelector('[type="checkbox"]'); //доступ к чекбоксу

    addForm.addEventListener('submit', (event) => { //1
        event.preventDefault(); //остановка действий браузера (не будет перезагружаться)

        let newFilm = addInput.value; //value - данные, которые ввел пользователь
        const favorite = checkbox.checked; //checked - отмеченная галочка

        if (newFilm) { //условие для того, чтоб не добавлялась пустая строка (записали - true)

            if (newFilm.length > 21) { //2
                newFilm = `${newFilm.substring(0, 22)}...`; //22 не включается
            }

            if (favorite) { //4
                console.log("Добавляем любимый фильм");
            }

            movieDB.movies.push(newFilm); //1
            sortArr(movieDB.movies);//сортируем по алфавиту

            createMovieList(movieDB.movies, movieList);
        }
        event.target.reset(); //очистили форму
    });

    const deleteAdv = (arr) => {
        arr.forEach(item => {
            item.remove();
        });
    };

    const makeChanges = () => {
        genre.textContent = 'драма';

        poster.style.backgroundImage = 'url("img/bg.jpg")';
    };

    const sortArr = (arr) => {
        arr.sort(); //сортируем по алфавиту
    };

    function createMovieList(films, parent) {
        parent.innerHTML = "";
        sortArr(films); //5

        films.forEach((film, i) => {
            parent.innerHTML += `
            <li class="promo__interactive-item">${i + 1} ${film}
                <div class="delete"></div>
            </li>
            `;
        });

        document.querySelectorAll('.delete').forEach((btn, i) => { //3
            btn.addEventListener('click', () => {
                btn.parentElement.remove(); //удаляет родителя
                movieDB.movies.splice(i, 1); //splice вырезает элемент (i - номер, 1 - кол-во)

                createMovieList(films, parent); //перестраивается нумерация после удаления (рекурсия на саму себя)
            });
        });
    }

    deleteAdv(adv);
    makeChanges();
    createMovieList(movieDB.movies, movieList);

});
```
6. Completed course on [udemy.com](https://www.udemy.com/) - [JavaScript + React course - from scratch to result](https://www.udemy.com/course/javascript_full/learn/lecture/14328446#overview)
7. Degree - **Master**
8. English Level - _Elementary_