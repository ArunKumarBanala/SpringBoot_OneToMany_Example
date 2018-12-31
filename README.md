# SpringBoot_OneToMany_Example
Implementing one to many relation between Post and Comment classes
----------------------------------------------------------------------

# Oracle-SQL Queries


create table post (id number(6), created_at TIMESTAMP, updated_at TIMESTAMP, content varchar2(100), description varchar2(250), title varchar2(100), constraint pk_postid primary key (id));

select * from post; desc post;

create SEQUENCE post_seq start with 1;

create or replace trigger post_dir before insert on post for each row

begin select post_seq.nextval into :new.id from dual; end;

drop table post;

create table comments (id number(6), created_at TIMESTAMP, updated_at TIMESTAMP, text varchar2(100), post_id number(6), constraint pk_commentid primary key (id), constraint fk_postid foreign key(post_id) references post (id));

create sequence comments_seq start with 1;

create or replace trigger comments_dir before insert on comments for each row begin select comments_seq.nextval into :new.id from dual; end;

select * from comments;

drop trigger comments_dir;

drop sequence comments_seq;

drop table comments;

-- 
