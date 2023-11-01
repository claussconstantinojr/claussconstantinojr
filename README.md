CREATE TABLE "Электронная почта"(
    "id_mail" VARCHAR(255) NOT NULL,
    "Адрес эл почты" VARCHAR(255) NOT NULL,
    "подтверждение адреса" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Электронная почта" ADD PRIMARY KEY("id_mail");
CREATE TABLE "Подтверждение опыта работы"(
    "id_indwork" VARCHAR(255) NOT NULL,
    "Трудовая книжка" TEXT NOT NULL,
    "Договор гпх" TEXT NOT NULL
);
ALTER TABLE
    "Подтверждение опыта работы" ADD PRIMARY KEY("id_indwork");
CREATE TABLE "ФИО"(
    "id_SNN" VARCHAR(255) NOT NULL,
    "Фамилия" VARCHAR(255) NOT NULL,
    "Имя" VARCHAR(255) NOT NULL,
    "Отчество" VARCHAR(255) NOT NULL,
    "Дата рождения" INTEGER NOT NULL
);
ALTER TABLE
    "ФИО" ADD PRIMARY KEY("id_SNN");
CREATE TABLE "Базы вакансий"(
    "id_vacation base" VARCHAR(255) NOT NULL,
    "ФИО" VARCHAR(255) NOT NULL,
    "Электронная почта" VARCHAR(255) NOT NULL,
    "Подтверждение личности" VARCHAR(255) NOT NULL,
    "Требуемая вакансия" VARCHAR(255) NOT NULL,
    "Диплом об окончании высшего образования" VARCHAR(255) NOT NULL,
    "Опыт работы" VARCHAR(255) NOT NULL,
    "Предпочтения по графику работы" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Базы вакансий" ADD PRIMARY KEY("id_vacation base");
CREATE TABLE "Требуемая вакансия"(
    "id_vacation" VARCHAR(255) NOT NULL,
    "Психолог" VARCHAR(255) NOT NULL,
    "Гипнолог" VARCHAR(255) NOT NULL,
    "Регрессолог" VARCHAR(255) NOT NULL,
    "Нутрициолог" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Требуемая вакансия" ADD PRIMARY KEY("id_vacation");
CREATE TABLE "Опыт работы"(
    "id_exp" VARCHAR(255) NOT NULL,
    "Место работы" VARCHAR(255) NOT NULL,
    "Занимаемая должность" VARCHAR(255) NOT NULL,
    "Время работы" INTEGER NOT NULL,
    "Подтверждение опыта работы" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Опыт работы" ADD PRIMARY KEY("id_exp");
CREATE TABLE "Диплом об окончании высшего образования"(
    "id_university" VARCHAR(255) NOT NULL,
    "Место обучения" VARCHAR(255) NOT NULL,
    "Направление обучения" VARCHAR(255) NOT NULL,
    "Продолжительность обучения" INTEGER NOT NULL,
    "Уровень образования" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Диплом об окончании высшего образования" ADD PRIMARY KEY("id_university");
CREATE INDEX "Диплом об окончании высшего образования_Место обучения_index" ON
    "Диплом об окончании высшего образования"("Место обучения");
CREATE INDEX "Диплом об окончании высшего образования_Направление обучения_index" ON
    "Диплом об окончании высшего образования"("Направление обучения");
CREATE TABLE "Подтверждение личности"(
    "id_indification" VARCHAR(255) NOT NULL,
    "Паспорт гражданина" TEXT NOT NULL,
    "свидетельство о рождении" TEXT NOT NULL
);
ALTER TABLE
    "Подтверждение личности" ADD PRIMARY KEY("id_indification");
CREATE TABLE "Предпочтения по графику работы"(
    "id_time" VARCHAR(255) NOT NULL,
    "8:00-17:00" TIMESTAMP(0) WITHOUT TIME ZONE NOT NULL,
    "17:00-02:00" TIMESTAMP(0) WITHOUT TIME ZONE NOT NULL
);
ALTER TABLE
    "Предпочтения по графику работы" ADD PRIMARY KEY("id_time");
ALTER TABLE
    "Опыт работы" ADD CONSTRAINT "Опыт работы_Подтверждение опыта работы_foreign" FOREIGN KEY("Подтверждение опыта работы") REFERENCES "Подтверждение опыта работы"("id_indwork");
ALTER TABLE
    "Базы вакансий" ADD CONSTRAINT "Базы вакансий_Требуемая вакансия_foreign" FOREIGN KEY("Требуемая вакансия") REFERENCES "Требуемая вакансия"("id_vacation");
ALTER TABLE
    "Базы вакансий" ADD CONSTRAINT "Базы вакансий_Электронная почта_foreign" FOREIGN KEY("Электронная почта") REFERENCES "Электронная почта"("id_mail");
ALTER TABLE
    "Базы вакансий" ADD CONSTRAINT "Базы вакансий_Предпочтения по графику работы_foreign" FOREIGN KEY("Предпочтения по графику работы") REFERENCES "Предпочтения по графику работы"("id_time");
ALTER TABLE
    "Базы вакансий" ADD CONSTRAINT "Базы вакансий_Опыт работы_foreign" FOREIGN KEY("Опыт работы") REFERENCES "Опыт работы"("id_exp");
ALTER TABLE
    "Базы вакансий" ADD CONSTRAINT "Базы вакансий_ФИО_foreign" FOREIGN KEY("ФИО") REFERENCES "ФИО"("id_SNN");
ALTER TABLE
    "Базы вакансий" ADD CONSTRAINT "Базы вакансий_Диплом об окончании высшего образования_foreign" FOREIGN KEY(
        "Диплом об окончании высшего образования"
    ) REFERENCES "Диплом об окончании высшего образования"("id_university");
ALTER TABLE
    "Базы вакансий" ADD CONSTRAINT "Базы вакансий_Подтверждение личности_foreign" FOREIGN KEY("Подтверждение личности") REFERENCES "Подтверждение личности"("id_indification");
